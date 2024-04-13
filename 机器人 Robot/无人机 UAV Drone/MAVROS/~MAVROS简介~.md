+ ROS官网上的MAVROS文档（很久没更新了）：[https://wiki.ros.org/mavros](https://wiki.ros.org/mavros)
+ Github：[https://github.com/mavlink/mavros](https://github.com/mavlink/mavros)

MAVROS是ROS与MAVLink协议之间的接口，由MAVLink官方开发，承担ROS与飞控之间的通讯桥梁，让无人机可以在Offboard模式下接收ROS发送的控制命令，同时ROS也可以获取到飞控模块FCU反馈的传感器数据。

严格意义上，MAVROS由三个软件包mavros、mavros_msgs、mavros_extras构成：

+ `mavros`：MAVROS的主节点和插件
+ `mavros_msgs`：MAVROS的用到的消息和服务类型定义
+ `mavros_extras`：一些和机器视觉有关的节点和插件

MAVROS提供的ROS接口以话题和服务的形式使用，大部分通过插件（Plugin）引入。

+ 订阅的话题：ROS --> FCU
+ 发布的话题：FCU --> ROS

注意MAVROS启动时，所有话题和服务都以`/mavros`命名空间开头，如`rc/in`实际为`/mavros/rc/in`

[[#MAVROS启动时的完整话题列表]]
[[#MAVROS启动时的完整服务列表]]

---
## MAVROS启动时的完整话题列表

![[Pasted image 20240326094501.png]]
![[Pasted image 20240326094555.png]]
![[Pasted image 20240326094648.png]]

---
## MAVROS启动时的完整服务列表

![[Pasted image 20240330104758.png]]
![[Pasted image 20240330104827.png]]
