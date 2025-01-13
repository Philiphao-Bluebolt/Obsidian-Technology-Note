+ 官方文档：[https://wiki.ros.org/nav_msgs](https://wiki.ros.org/nav_msgs)

`nav_msgs`包含机器人可能会用到的导航相关信息，如最常用的里程计信息`Odometry`

---
## `Odometry`：里程计信息

`nav_msgs/Odometry`一般是IMU、双目相机等定位传感器反馈的消息类型，它包含了机器人的参考固定坐标、自身的坐标、位姿以及速度旋量信息。

`header`的`frame_id`非常重要，它是里程计信息固定坐标参考系，用于确定绝对位置；`child_frame_id`是机体坐标。

```msg
Header header  
string child_frame_id  
geometry_msgs/PoseWithCovariance pose  
geometry_msgs/TwistWithCovariance twist
```