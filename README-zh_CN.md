<img src='http://gridstudio.io/image/logo-grid.svg' width='200px' style='margin-bottom: 30px;'>

Grid studio是一个网页版电子表格应用,并且集成Python语言。

这个工具致力于提供加载、清洗、处理与可视化数据的一体化工作流。通过采用Go语言编写的电子表格后端，以及用于处理数据的集成Python运行时环境。

### 软件架构

应用分两部分

1. The (centralized) workspace manager
    1. CRUD interface for creating, copying, editing and deleting workspaces.
    1. Proxy to send traffic to the right workspace environment (part 2)
1. Workspace Go execution environment
    1. Go cell parsing and evaluating spreadsheet backend
    1. Node.js terminal session
    1. Python interpreter integration

For more details about each part check out the code in the repository. If anything is unclear (or unreadable - not all code is equally pretty!) make an issue and details will be provided.

### 安装

To run Grid studio locally refer to the <a href="https://github.com/ricklamers/gridstudio/wiki/Installation">Installation</a> page of the Wiki.

It comes down to pulling the latest Grid studio Docker image that has all dependencies configured (mainly: Go language, Python 3 with packages, Node.js) and starting the Docker container.

For more information check out our <a href="https://github.com/ricklamers/gridstudio/wiki">Wiki</a>.

<b>If don't want to install Grid studio locally you can try out the beta of the hosted version here: <a href="https://dashboard.gridstudio.io">https://dashboard.gridstudio.io</a>.</b>

### 构建  

    Installing Grid studio locally is very simple:


    1. Clone the repository with this command:

    git clone https://github.com/ricklamers/gridstudio

    2. Run the bash script (on Windows use e.g. Git Bash) with this command:

    cd gridstudio && ./run.sh

    3. Go to http://127.0.0.1:8080 in your browser. Note! Username: admin password: admin   

### 开发技术栈

docker
    ubuntu 18.04
terminal server
    xterm.js
web server
    go

python

