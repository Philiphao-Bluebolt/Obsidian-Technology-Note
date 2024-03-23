+ ROS官网上的MAVROS文档：[https://wiki.ros.org/mavros](https://wiki.ros.org/mavros)

无人机的Offboard模式需要机载电脑上ROS控制程序发送命令才能成功运行，在这个过程中，MAVROS就充当了ROS环境与飞控模块之间的通讯桥梁，它是由MAVLink官方开发的ROS系列软件包。

严格意义上，MAVROS由三个软件包mavros、mavros_msgs、mavros_extras构成：

+ mavros：MAVROS的主节点和插件
+ mavros_msgs：MAVROS的用到的消息和服务类型定义
+ mavros_extras：一些和机器视觉有关的节点和插件
