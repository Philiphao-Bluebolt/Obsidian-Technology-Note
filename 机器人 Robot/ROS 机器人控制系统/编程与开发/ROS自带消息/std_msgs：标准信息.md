+ 官方文档：[http://wiki.ros.org/std_msgs](http://wiki.ros.org/std_msgs)

`std_msgs`提供了一些最基本的消息类型给其他更复杂的消息调用。

---

## `Header`：序号、时间戳和坐标名称

`Header`会被其他消息的带戳（Stamped）变体调用，它用于储存三个重要信息：

+ `seq`：消息的发布序号（第几条消息）
+ `time`：发布时间，分为两部分：“自开始运行后的秒数”、“自上一秒的纳秒数”
+ `string`：消息发布所在的坐标系，是TF跟踪坐标系的依据

```msg
uint32 seq
time stamp
string frame_id
```

---

## `Empty`：空消息

`Empty`不携带任何数据，一般只用于触发进入订阅者的回调函数。（订阅者的回调函数只有在接收到消息时才会触发执行）