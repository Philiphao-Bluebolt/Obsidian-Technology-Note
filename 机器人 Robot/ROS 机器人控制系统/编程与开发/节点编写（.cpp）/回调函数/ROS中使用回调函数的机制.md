ROS中有多种机制使用回调函数，最常见的就是订阅者的回调函数

---

+ 订阅者（Subscriber）及其回调函数：[[订阅者 Subscriber]]

```cpp
ros::Subscriber state_sub = nh.subscribe<mavros_msgs::State>("/mavros/state", 100, stateCallback);
```

```cpp
void stateCallback(const mavros_msgs::State::ConstPtr& state_msg)
{
    current_mode = state_msg->mode;
}
```

---

+ 服务器（Server）及其回调函数：

```cpp



```

---

+ 计时器（Timer）控制的周期回调函数：[[周期回调函数 Periodic Callback]]

```cpp
ros::Timer  my_timer = nh.createTimer(ros::Duration(0.5), timerCallback);
```

```cpp
void timerCallback(const ros::TimerEvent&)
{
	ROS_INFO("Triggered");
}
```