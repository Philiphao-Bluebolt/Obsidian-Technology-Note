ROS提供了两种常用编程语言的开发接口：`ROScpp`（C++）和`ROSpy`（Python）

---
## C++接口

+ 官方roscpp文档：[https://wiki.ros.org/roscpp/Overview](https://wiki.ros.org/roscpp/Overview)

C++是ROS官方稳定支持的两种开发语言之一，相比Python而言，C++实现的ROS程序的运行效率更高，在社区也更为常用。使用C++开发时，参数服务器、发布者、订阅者、消息、服务端、客户端、服务类型等通讯方式通过面向对象实现。

ROS提供的`roscpp`功能包提供了编写节点以及调用常见功能的函数和类，ROS节点的C++源码必须包含以下头文件，以确保`roscpp`的相关函数和类可以被成功调用。

```cpp
#include <ros/ros.h>
```

编写完成以后，C++源码需要经过编译：[[3. 编译C++文件]]

---
## Python接口

+ 官方rospy文档：[http://wiki.ros.org/rospy](http://wiki.ros.org/rospy)

ROS的Python接口称为`rospy`，虽然Python在ROS开发领域比C++用得少，但在机器学习领域很常用，因此涉及机器学习的机器人系统就需要用到ROS的Python接口

调用Python的ROS接口：

```python
import  rospy
```

### 虚拟环境Python版本冲突

若Python的Anaconda虚拟环境的版本与ROS使用的Python版本冲突，会导致节点无法完成初始化

+ 参见：[[Anaconda - Conda：虚拟环境及包管理#与ROS共存]]

---
## 对比

ROS在C++和Python的接口使用方法相同，只是语法上有一些区别


