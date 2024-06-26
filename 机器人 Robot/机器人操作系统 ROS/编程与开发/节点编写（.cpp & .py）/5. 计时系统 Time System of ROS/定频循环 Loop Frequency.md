
---
## C++

+ 官方文档：[https://docs.ros.org/en/kinetic/api/rostime/html/classros_1_1Rate.html](https://docs.ros.org/en/kinetic/api/rostime/html/classros_1_1Rate.html)
+ 相关函数及类：`ros::Rate`、`ros::Rate.sleep()`

`ros::Rate`定义的定频对象可以用于控制代码中循环体的执行频率，定义时传入构造函数的参数是这个定频对象的控制频率，单位为Hz。

```cpp
ros::Rate my_rate(20.0);
```

在一个循环体的结尾处调用定频对象的成员函数`sleep()`，可以调整循环的周期。

在下面的代码中，如果原本一次循环只需要0.01s完成，`my_rate.sleep()`会等待0.04s，将一次循环的周期延长到0.05s，对应之前设置的20Hz频率。

```cpp
while(ros::ok())
{
	...
	ros::spinOnce();
	my_rate.sleep();
}
```

---
## Python