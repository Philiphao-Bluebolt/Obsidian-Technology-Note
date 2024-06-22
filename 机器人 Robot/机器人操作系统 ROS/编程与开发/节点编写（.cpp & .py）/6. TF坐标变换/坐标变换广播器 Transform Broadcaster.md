坐标变换广播器（Transform Broadcaster）通过发送一个变换消息`TransformStamped`，建立父坐标系到子坐标系的变换关系

+ 普通动态广播器（Transform Broadcaster），适用于位置动态改变的坐标变换关系，比如说世界坐标系到机器人坐标系的变换，使用时需要以一定频率持续发布。
+ 静态广播器（Static Transform Broadcaster），适用于一对相对变换固定的坐标系，比如说机器人机身到传感器的坐标变换，使用时只需要发布一次。

---
## C++


---
## Python

### 静态广播器

+ 官方教程：[Writing a tf2 static broadcaster (Python)](https://wiki.ros.org/tf2/Tutorials/Writing%20a%20tf2%20static%20broadcaster%20%28Python%29)