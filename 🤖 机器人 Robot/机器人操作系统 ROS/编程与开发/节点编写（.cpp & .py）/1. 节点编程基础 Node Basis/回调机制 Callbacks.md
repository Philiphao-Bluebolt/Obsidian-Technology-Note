回调函数是ROS中常见的一种机制

订阅者Subscriber创建后，依靠定义在`main()`外的回调函数（Callback Function）对接收的数据进行处理，但在C++中回调函数并不会自己执行，因此需要一种方法来启动回调函数

ROS中有多种机制使用回调函数，最常见的就是订阅者

+ 订阅者回调函数（Subscriber Callbacks）：[[订阅者 Subscriber]]
+ 服务器回调函数（Server Callbacks）
+ 周期回调函数（Periodic Callbacks）
+ 动作回调函数（Action Callbacks）

Python不需要Spin()函数唤起回调

---
## C++

+ 官方文档：[https://wiki.ros.org/roscpp/Overview/Callbacks%20and%20Spinning](https://wiki.ros.org/roscpp/Overview/Callbacks%20and%20Spinning)
+ 相关函数及类：`ros::spin()`、`ros::spinOnce()`

### 持续回调：ros::spin()

`ros::spin()`函数一般写在`main()`主函数的结尾处，一但开始执行，节点进入回调事件循环，循环调用各订阅者的回调函数，直到节点被关闭。因此，`main()`中在`ros::spin()`函数之后的代码是不会执行的

```cpp
int main(int argc,  char** argv)
{
	...
	ros::spin();
	return 0;
}
```

### 单次回调：ros::spinOnce()

`ros::spinOnce()`函数在执行时只调用一次回调函数，完成后会继续执行`main()`中的代码，一般会配合`while`循环使用以确保对回调函数的持续调用。

```cpp
int main(int argc,  char** argv)
{
	...
	ros::Rate rate(20.0);
	while (ros::ok())
	{
		...
		ros::spinOnce();
		rate.sleep();
	}
	return 0;
}
```

---
## Python

Python的线程运行原理和C++不同，并不需要使用Spin()函数唤起回调