+ 官方roscpp文档：[https://wiki.ros.org/roscpp/Overview](https://wiki.ros.org/roscpp/Overview)

C++是ROS官方稳定支持的两种开发语言之一，相比Python而言，C++实现的ROS程序的运行效率更高，在社区也更为常用。使用C++开发时，参数服务器、发布者、订阅者、消息、服务端、客户端、服务类型等通讯方式通过面向对象实现。

ROS节点的C++源码必须包含以下头文件，以确保roscpp的相关函数和类可以被成功调用。

```cpp
#include <ros/ros.h>
```