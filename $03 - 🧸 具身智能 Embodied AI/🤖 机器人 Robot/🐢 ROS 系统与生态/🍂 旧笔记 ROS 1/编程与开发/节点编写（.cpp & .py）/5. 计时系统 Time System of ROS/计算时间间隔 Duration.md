ROS编程时经常需要使用计时功能，最常见的使用场景是计算过去的某个时刻$t_0$到现在的时间间隔

---
## C++

+ 相关函数和类：`ros::Time`、`ros::Time::now()`、`ros::Duration::toSec()`

首先记录一个时刻，这里的函数`ros::Time::now()`返回一个取值为现在时刻的时间对象

```cpp
ros::Time  record_time = ros::Time::now();
```

获取$t_0$时刻到现在的时间间隔，并转换为秒数：

```cpp
ros::Duration  my_duration = ros::Time::now() - record_time;
double my_duration_sec = my_duration.toSec();
```

---
## Python

+ 相关函数和类：`rospy.Time`、`rospy.Time.now()`、`rospy.Duration.to_sec()`

记录时刻

```python
record_time = rospy.Time.now()
```

获取时间间隔，转换为秒数

```python
my_duration = rospy.Time.now() - record_time
my_duration_sec = my_duration.to_sec()
```