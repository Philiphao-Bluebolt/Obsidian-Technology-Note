+ 官方文档：[http://wiki.ros.org/std_msgs](http://wiki.ros.org/std_msgs)

`std_msgs`提供了一些最基本的消息类型给其他更复杂的消息调用，涉及的消息一般用于储存单个的整型、浮点数、字符、字符串等简单数据。

---
## `Header`：序号、时间戳和坐标名称

`Header`会被其他消息的带戳（Stamped）变体调用，它用于储存三个重要信息：

+ `seq`：消息的发布序号（第几条消息）
+ `stamp`：发布时间，用于同步，详见：[[~ROS中的时间系统~]]
+ `frame_id`：消息发布所在的坐标系，是TF跟踪坐标系的依据

```msg
uint32 seq
time stamp
string frame_id
```

---
## `Empty`：空消息

`Empty`不携带任何数据，一般只用于触发进入订阅者的回调函数。（订阅者的回调函数只有在接收到消息时才会触发执行）

---
## 单数据消息

这些消息的结构都很简单，内部只有一个以各自类型定义的`data`成员

+ 布尔型：`Bool`
+ 字节：`Byte` 、`Char`
+ 有符号整型：`Int8`、`Int16`、`Int32`、`Int64`
+ 无符号整型：`UInt8`、`UInt16`、`UInt32`、`UInt64`
+ 浮点型：`Float32`、`Float64`