#### Calibration
##### Camera Calibration
###### Reminder

改变raw image发布频率

* 方法一（文件修改）：
```bash
roscd duckietown/config/baseline/pi_camera/decoder_node
vim default.yaml
```

* 方法二（launch文件）：
```bash
roscd duckietown/launch
cp camera.launch camera2.launch
vim camera2.launch
```
修改launch文件为：
```bash
<launch>
    ...
    <arg name="rect" ... />
    <arg name="freq" default="2" />
    ...
    <!--decoder_node-->
    	...
    	<include file="$(find pi_camera)/launch/decoder_node.launch">
			...
    	</include>
    	<param name="$(arg veh)/decoder_node/publish_freq" value="$(arg freq)" />
    ...
</launch>
```
运行时，输入以下命令：
```bash
roslaunch camera2.launch veh:=[id] raw:=true rect:=true freq:=10
```

###### Intrinsic Calibration
前期准备

* 打印校正的格点纸（[pdf](https://github.com/yzxky/Duckietown-Tutorial/blob/master/3.duckietown/calibration_pattern.pdf)），该格点纸在intrinsic callibration和extrinsic callibration中均有用

* 保证电脑与小车的ros网络环境配置正确，参考[memorial.md](https://github.com/yzxky/Duckietown-Tutorial/blob/master/3.duckietown/memorial.md)

* 下载duckietown工程（[简化版](https://github.com/yzxky/Duckietown_Compressed_ws)或[原版](https://github.com/duckietown/Software)）并编译

内部校正

* 启动小车端相机，注意raw需设为true
```bash
roslaunch duckietown camera.launch veh:=duckiebot[id] raw:=true
```

* 在电脑端运行标定程序
```bash
roslaunch duckietown intrinsic_calibration.launch veh:=duckiebot[id]
```

##### Extrinsic calibration
```bash
roslaunch duckietown camera.launch veh:=duckiebot[id] raw:=true
```

```bash
roslaunch ground_projection ground_projection.launch veh:=duckiebot[id] local:=true
```

```bash
rosservice call /duckiebot[id]/ground_projection/estimate_homography
```