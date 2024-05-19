周期回调函数（Periodic Callbacks）可以通过定义计时器Timer以一定频率周期性地触发

---
## C++

+ 官方教程：[https://wiki.ros.org/roscpp_tutorials/Tutorials/Timers](https://wiki.ros.org/roscpp_tutorials/Tutorials/Timers)
+ 官方文档：[https://wiki.ros.org/roscpp/Overview/Timers](https://wiki.ros.org/roscpp/Overview/Timers)
+ 相关函数及类：`ros::Timer` 

第一个参数指定触发回调的周期（秒）

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
