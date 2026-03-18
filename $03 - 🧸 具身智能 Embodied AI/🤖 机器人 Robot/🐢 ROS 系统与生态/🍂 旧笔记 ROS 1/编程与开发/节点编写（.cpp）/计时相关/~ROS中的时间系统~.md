+ 官方文档：[https://wiki.ros.org/roscpp/Overview/Time](https://wiki.ros.org/roscpp/Overview/Time)
+ 相关类：`ros::Time`（`ros::WallTime`）、`ros::Duration`（`ros::WallDuration`）、`ros::Rate`（`ros::WallRate`）、`ros::Timer`（`ros::WallTimer`）

---
## Unix时间

+ Wikipedia：[Unix时间](https://zh.wikipedia.org/wiki/UNIX%E6%97%B6%E9%97%B4)
+ 转换器：[https://unixtime.org/](https://unixtime.org/)

ROS使用UNIX时间，原始时间数据含义为从UTC1970年1月1日0时0分0秒起至现在的总秒数。

+ `ROS_INFO`和`ROS_WARN`输出的时间

![[Pasted image 20240401100711.png]]

---
## 时间格式

ROS内部定义了两种和时间相关的变量类型：

+ 时刻`time`，在`roscpp`中为`ros::Time`
+ 时间间隔`duration`，在`roscpp`中为`ros::Duration`

他们的定义是类似的，唯一不同是`duration`可以取负值。`sec`指的是秒数的整数部分，`nsec`则是表示小数部分纳秒

```msg
int32 sec
int32 nsec
```

注意真实的Unix秒数是

```cpp
unix_sec = sec + nsec * 10e-9
```

时刻与时刻相加的运算是没有实际含义的

---
## 计时系统

ROS内部有两套计时系统

+ ROS时间（ROS Time）：直接运行时与现实时间同步，运行ROSbag回放或某些仿真分析时，则以当时记录的时间为准。
+ 现实时间（Wall Time）：总是和机器系统的时间同步

一般来说，我们会使用ROS时间，若的确需要使用现实时间，则调用Wall版本的时间类`ros::WallTime`、`ros::WallDuration`、`ros::WallRate`，两种计时系统的接口除名字以外是完全一样的 。

---
## `/clock`话题

+ 官方文档：[http://wiki.ros.org/Clock](http://wiki.ros.org/Clock)

`/clock`在仿真环境或话题回放时提供不同于现实时间的ROS时间