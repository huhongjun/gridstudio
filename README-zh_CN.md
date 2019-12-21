<img src='http://gridstudio.io/image/logo-grid.svg' width='200px' style='margin-bottom: 30px;'>

Grid studio是一个Web版电子表格应用软件，完全集成Python编程语言。

该软件致力于提供加载、清洗、操作和可视化数据的一体化工作流。通过采用Go语言编写的电子表格后端，以及用于处理数据的集成Python运行时环境。

<a href="https://app.slack.com/client/TBZFHQPGS/CC0GKCMAB?cdn_fallback=1"> Slack Grid-community</a>

### 软件架构

应用分两部分

1. (集中的)工作空间管理器
    1. 工作空间的增删改和拷贝.
    1. 发送消息到对应的工作空间环境(part 2)
2. 工作空间的go执行环境
    1. Go实现的单元格解析与计算电子表格后端
    1. Node.js终端会话
    1. Python解释器集成

### 安装

To run Grid studio locally refer to the <a href="https://github.com/ricklamers/gridstudio/wiki/Installation">Installation</a> page of the Wiki.

It comes down to pulling the latest Grid studio Docker image that has all dependencies configured (mainly: Go language, Python 3 with packages, Node.js) and starting the Docker container.

For more information check out our <a href="https://github.com/ricklamers/gridstudio/wiki">Wiki</a>.

<b>If don't want to install Grid studio locally you can try out the beta of the hosted version here: <a href="https://dashboard.gridstudio.io">https://dashboard.gridstudio.io</a>.</b>

### 构建与安装、运行  

    本地安装Grid studio很简单:

    1. 克隆github仓库：
        git clone https://github.com/ricklamers/gridstudio
    2. 执行bash脚本(Windows上使用Git Bash):
        cd gridstudio && ./run.sh
    3. 浏览器中打开http://127.0.0.1:8080 ，用户名称: admin，密码： admin   

    容器构建
        cd grid-app && sudo ./build.sh  
        docker push 192.168.1.114:5000/busybox:v1

### 开发技术栈

docker
    ubuntu 18.04
Xterm.js

    terminal server
        Xterm.js is a front-end component written in TypeScript that lets applications bring fully-featured terminals to their users in the browser. It's used by popular projects such as VS Code, Hyper and Theia.Xterm.js is not bash. Xterm.js can be connected to processes like bash and let you interact with them (provide input, receive output).  
    xterm client  

web server  
    go语言  
    功能  
        workspace管理  
        文件服务器(上传\加载\主机文件访问)  
        Python集成  
        电子表格处理  
proxy  
    go  
python  
    脚本运行  
    预定义函数 =》1个init.py  

### 文件说明  

/docu  huhongjun新增文档目录  
/examples  Python脚本样例  
    estimate_normal.py  
    scrape.py  
/grid-app  
    /detector  
        detector.go
    /proxy  
        /db                     sqllite3数据库
        /logs
            /sessionlogs        日志
        /sessionmanager
        /static
        /userdata
        /websocketproxy
        manager.do
        run-manager-proxy.sh    
    /python
    /static
    /terminal-server
        /xterm.js   xterm客户端
        app.js      xterm服务器，nodejs expressWs
    /working-files
    build.sh
    client.go
    dockerfile
    grid.go         电子表格
    hub.go          ws hub
    main.go         go服务器入口
    parse.go        电子表格函数执行
    python.go       Python解释器接受执行脚本并处理python执行输出
    tests.go        自动化单元测试
destroy.sh  docker删除容器
run.sh      docker启动容器
shutdown.sh docker关闭容器
