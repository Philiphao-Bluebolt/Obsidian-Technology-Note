参见[[3. 话题与消息 Topic & Message (msg)]]

---
## C++

+ 官方教程：[https://wiki.ros.org/ROS/Tutorials/WritingPublisherSubscriber%28c%2B%2B%29](https://wiki.ros.org/ROS/Tutorials/WritingPublisherSubscriber%28c%2B%2B%29)
+ 官方文档：[https://wiki.ros.org/roscpp/Overview/Publishers%20and%20Subscribers](https://wiki.ros.org/roscpp/Overview/Publishers%20and%20Subscribers)
+ 相关函数及类：`ros::Publisher`、`nh.advertise<>()`

创建一个发布者对象的示例代码如下。

+ `topic_pub`：代码中发布者对象的名称，仅在源代码内部使用，约定俗成格式`xxx_pub`
+ `nh`：节点句柄的名称
+ `std_msgs::String`：发布的话题所使用的消息类型
+ `topic_name`：话题在ROS系统的名称，可以被launch文件重映射更改
+ `100`：话题寄存器的大小

```cpp
ros::Publisher  topic_pub = nh.advertise<std_msgs::String>("topic_name", 100);
```

调用发布者对象的成员函数`publish()`将代码中事先定义好的信息`my_text`发布到话题中，就完成了一次发布。

```cpp
std_msgs::String  my_text = "I love ROS";

pub.publish(my_text);
```

特别的，如果需要在回调函数中进行发布，创建发布者时需要将声明和定义分开，在全局空间或者头文件中声明，在`main()`函数中定义

```cpp
ros::Publisher  pub;

int main(int argc, char **argv){
    ...
    pub = nh.advertise<std_msgs::String>("topic_name", 100);
}
```

