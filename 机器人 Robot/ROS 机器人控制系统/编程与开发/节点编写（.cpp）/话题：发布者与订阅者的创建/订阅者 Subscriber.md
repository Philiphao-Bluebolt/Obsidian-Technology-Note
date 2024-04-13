+ 官方教程：[https://wiki.ros.org/ROS/Tutorials/WritingPublisherSubscriber%28c%2B%2B%29](https://wiki.ros.org/ROS/Tutorials/WritingPublisherSubscriber%28c%2B%2B%29)
+ 官方文档：[https://wiki.ros.org/roscpp/Overview/Publishers%20and%20Subscribers](https://wiki.ros.org/roscpp/Overview/Publishers%20and%20Subscribers)
+ 相关函数及类：`ros::Subscriber`、`nh.subscribe<>()`

---

创建订阅者对象与创建发布者格式类似，但需要指定回调函数（下面例子中的`str_callback`）才能接收到订阅话题传回的消息

声明时可省略消息类型；`topic_name`是订阅话题的名称（注意不要包含斜杠`/`）

```cpp
ros::Subscriber  sub = nh.subscribe<std_msgs::String>("topic_name", 100, str_callback);
```

下面是订阅者的回调函数的基本结构：订阅者的回调函数接受一个消息的结构体常指针`const <消息名称>::ConstPtr& msg`，在函数内部通过指针寻址符`msg->data`访问订阅者接收到的消息类内部的成员值`data`。

```cpp
void  str_callback(const std_msgs::String::ConstPtr&  msg){

    ROS_INFO("I heard: [%s]", msg->data.c_str());
}
```

如果订阅者订阅的话题上没有新的消息发布，则回调函数不会被调用，这个特性常用于构建触发器。