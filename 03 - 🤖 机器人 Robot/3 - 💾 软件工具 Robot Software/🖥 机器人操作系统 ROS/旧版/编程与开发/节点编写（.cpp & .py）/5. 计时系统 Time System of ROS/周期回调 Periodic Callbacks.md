周期回调函数（Periodic Callbacks）可以通过定义计时器Timer以一定频率周期性地触发

---
## C++

+ 官方教程：[https://wiki.ros.org/roscpp_tutorials/Tutorials/Timers](https://wiki.ros.org/roscpp_tutorials/Tutorials/Timers)
+ 官方文档：[https://wiki.ros.org/roscpp/Overview/Timers](https://wiki.ros.org/roscpp/Overview/Timers)
+ 相关函数及类：`ros::Timer` 

新建周期回调对象，第一个参数指定触发回调的周期（秒），第二个参数是回调函数

```cpp
ros::Timer  my_timer = nh.createTimer(ros::Duration(0.5), timerCallback);
```

回调函数的格式如下：

```cpp
void timerCallback(const ros::TimerEvent& e)
{
	ROS_INFO("Triggered");
}
```

---
## Python

+ 相关函数及类：`rospy.Timer`

新建周期回调对象

```python
my_timer = rospy.Timer(rospy.Duration(0.5), timer_callback)
```

回调函数

```python
def timer_callback(e):
	rospy.loginfo("Triggered")
```