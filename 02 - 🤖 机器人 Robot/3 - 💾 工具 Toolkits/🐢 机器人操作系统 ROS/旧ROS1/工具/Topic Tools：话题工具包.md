+ 官方文档：[https://wiki.ros.org/topic_tools](https://wiki.ros.org/topic_tools)

Topic Tools是一个简单的命令行话题功能包，提供了一些常用话题节点

---
## 话题转发：`relay`

将话题A的消息转发到话题B，两者的消息类型必须相同

```bash
rosrun  topic_tools  relay  /topic_a  /topic_b
```

---
## 话题