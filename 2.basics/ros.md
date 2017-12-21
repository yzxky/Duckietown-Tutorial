#### ROS基础
##### 整体架构
ROS基本结构与通信机制

* master: 类似于一个网域内的路由器，所有的程序节点都需要和master通信，在ros程序运行时，master节点必须启动
* node： 节点，一般来说，一个程序，就是一个节点。节点间可相互通信，发送msg或者srv。
* msg：一种类似于udp的通信机制，发送的内容可以被网域内所有节点接收
	* topic：发送msg的广播名称，要接收指定msg，需保证topic名一致
	* subscriber: msg接收方
	* publisher：msg发送方
* srv：一种类似于tcp的通信机制，发送方先request，接收方给出response，是双向的连接
	* service：发送srv的名称
	* req：request，
	* res：response
	* client：发送req给server，等待res
	* server：接收req，回复res

ROS工程的基本框架
* catkin: 一种工程的组织方式，也可以理解为一种工具  
  ROS工程一般都采用catkin workspace的方式
* workspace: 工作空间，一般是文件目录的最上极
* workspace中一般包括三个文件夹：
	* build：编译文件夹
	* devel：development，里面有一个文件比较重要**setup.bash**  
	 重要指令：source devel/setup.bash
    * src: 放置包和源码
* package: 程序包，放置在workspace中的src文件夹内，每个程序包可以看作一个单独的工程（project）
	* package.xml: 包属性配置文件
	* CMakeLists.txt: cmake配置文件，一般C++程序使用，改写比较麻烦
	* scripts: 脚本文件夹，存放python文件
	* src：源码文件夹，存放C++文件及头文件
	* msg: 消息文件夹，存放msg
	* srv： 服务文件夹，存放srv

##### ROS工程创建及编译
* 新建workspace
```bash
mkdir -p catkin_ws/src
cd catkin_ws/src
catkin_init_workspace #一定在src文件里初始化
```

* 编译工程
```bash
cd catkin_ws #更改路径至工作空间
catkin_make
```

* 新建一个package
```bash
cd catkin_ws/src
catkin_create_pkg [package_name] roscpp rospy std_msgs
```
 package的属性可以打开package.xml查看及修改

* 之后就可以在package内组织代码等


##### 编写及运行ROS程序
编写简单的publisher和subscriber  
参见ros tutorial教程([C++](wiki.ros.org/ROS/Tutorials/WritingPublisherSubscriber(c%2B%2B), [Python](wiki.ros.org/ROS/Tutorials/WritingPublisherSubscriber(python))

