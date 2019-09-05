
# 功能计划

    * 作为python脚本实验web-ide，类似jupyter notebook，但是一数据为中心 =》workspace集合终端、文件管理和代码（数据+脚本）
    * 定制数据处理Web应用 =》workspace组合多个csv和sheet；菜单栏添加定制菜单，对应一段python代码；context menu添加定制功能
    * 集成NER

# 工作日志

## 2019.09.05 星期四
  
  portainer帮助调试，可以看到日志，可以进入终端
  vscode docker插件可以菜单操作进入容器终端  
  界面 =》补充其他界面，标注主界面

## 2019.08.22

    构建docker => 构建成功
    探索其他功能 =》 函数定义，加载csv，批量数据处理，集成ner
    技术架构
    ToDo：go webserver中的websocket，python如何运行的

## 2019.08.21

    github下载源码=》ubuntu 16.04 + vscode 1.17.1环境=》新建中文readme
    ./run.sh => 浏览器打开 =》运行examples中的python源码 =》可以逐行执行；可以执行选择代码

# bugs

    # sudo ./build.sh  
    pip -i https://mirrors.aliyun.com/pypi/simple/
