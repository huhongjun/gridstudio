FROM ubuntu:18.04 as base

# 静默安装
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections

# 安装必备软件
RUN apt clean && apt update && \
apt install -y software-properties-common build-essential wget python3-pip locales curl git

# # TODO: see if any locale issues arise
# # RUN sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen && \
# #     locale-gen
# # ENV LANG en_US.UTF-8  
# # ENV LANGUAGE en_US:en  
# # ENV LC_ALL en_US.UTF-8  

# 安装go语言环境
RUN cd /tmp && \
wget https://dl.google.com/go/go1.12.5.linux-amd64.tar.gz && tar -C /usr/local -xzf go1.12.5.linux-amd64.tar.gz
ENV PATH /usr/local/go/bin:${PATH}

# 安装Python3.7，源ppa (快速)
RUN add-apt-repository ppa:deadsnakes/ppa && apt update && apt install -y python3.7

# 疑问？copy over all files to /home/source/
WORKDIR /home/source/
COPY . /home/source/

# 安装python + dependencies + nodejs
# apt install -y python3-tk && \
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash - && \
apt install -y nodejs

# 安装Python包：numpy pandas matplotlib scipy scikit-learn
RUN python3.7 -m pip install --upgrade pip numpy pandas matplotlib scipy scikit-learn

# python3.7 -m pip install tensorflow

# TODO: think about how to run terminal-server, probably multiple terminal-servers with parameters (one for each workspace)
# create /home/run/ directory to run terminal nodejs project from
RUN mkdir /home/run/
COPY ./terminal-server/ /home/run/terminal-server/

# install required NPM packages for term.js
WORKDIR /home/run/terminal-server/
RUN npm install --no-cache

# create work directory
RUN mkdir /home/user/

# 在/home/source下安装go语言依赖包
WORKDIR /home/source/

RUN go get -d -v ./...

# build manager.go once to speed up consecutive go builds
WORKDIR /home/source/proxy/
RUN go build manager.go
RUN rm ./manager

# expose ports
EXPOSE 8080
EXPOSE 4430

WORKDIR /home/source/proxy/

# 容器默认执行命令
CMD ["bash","run-manager-proxy.sh"]