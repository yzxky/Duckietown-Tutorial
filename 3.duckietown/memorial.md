###Duckietown备忘录
##### 修改小车主机名
* 根据小车标签修改主机名
```Bash
sudo vim /etc/hostname
sudo vim /etc/hosts
```

* 修改文件内主机名为duckiebot[id]，其中[id]为小车上标签数值

##### 远程连接duckiebot
* 将笔记本电脑与duckiebot置于同一网域内
```Bash
ssh duckiebot@duckiebot[id].local
```
或
```Bash
ssh duckiebot@[ip_address]
```

* duckiebot默认密码为duckiebot

##### 修改machines文件
* 进入catkin\_ws中的duckietown包
直接cd进目录
或
```Bash
roscd duckietown
```
* 修改machines文件
在文件中添加
```bash
<machine name="duckiebot[id]" address="duckiebot[id].local" user="duckiebot" env-loader="$(arg env_script_path)"/>
```

##### 启动驱动模块
* 调用duckietown驱动模块
```Bash
roslaunch duckietown joystick.launch veh:=duckiebot[id]
```

* veh为joystick.launch内定义的参数，即车辆名称
* 可以通过rosgraph查看节点间相互关系及发送的topic名称
* 控制小车运动的topic名为:/duckiebot[id]/joy\_mapper\_node/car\_cmd

##### 启动摄像头
* 启动摄像头
```Bash
roslaunch duckietown camera.launch veh:=duckiebot[id]
```
或
```Bash
roslaunch duckietown camera.launch veh:=duckiebot[id] raw:=true rect:=true
```

* veh: 车辆名称
* raw: 是否发布原始图像msg
* rect： 是否启动校正节点
* 摄像头msg可以通过rqt\_image\_view指令查看，下拉菜单中的名称即为对应图片的topic名

