静态坐标变换描述一组固定的坐标系变换关系，在ROS中可以通过调用TF提供的节点实现，也可以通过编程实现

---
## TF静态变换节点

TF静态变换节点`static_transform_publisher`常使用启动文件激活，输入的参数`args`依次分别是

+ XYZ坐标平移量
+ ZYX欧拉旋转角（弧度）
+ 父坐标名称
+ 子坐标名称
+ 发布频率

```xml
<node pkg="tf" type="static_transform_publisher" name="tf_parent_to_child" args="0 0 0 0 0 0 parent child 1000"/>
```

---
## 编程实现

参见[[坐标变换广播器 Transform Broadcaster]]