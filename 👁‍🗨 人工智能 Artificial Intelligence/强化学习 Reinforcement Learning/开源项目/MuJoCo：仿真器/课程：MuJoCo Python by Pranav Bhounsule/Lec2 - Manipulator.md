+ 课程链接：[MuJoCoPy Lec 2a: 2D Manipulator modeling (Part 1 of 2)](https://www.youtube.com/watch?v=Fiq_hpaoeH0&ab_channel=PranavBhounsule)
+ XML文档：[XML Reference](https://mujoco.readthedocs.io/en/stable/XMLreference.html)

这节课的主要内容是搭建一个可操纵的二连杆机械臂，分为建模和编程两部分

![[Pasted image 20240424110435.png]]

---
## 创建连杆一

用圆柱体作为连杆，调整圆柱体的尺寸和位姿，使其绕世界坐标系的Z轴旋转

关节的类型为`hinge`，表示转动副，其转轴向量`axis`和位置`pos`的定义相对于`<body>`的体坐标系

```xml
<body pos="0.5 0 0.1" euler="0 90 0">
  <joint type="hinge" axis="-1 0 0" pos="0 0 -0.5"/>
  <geom type="cylinder" size="0.05 0.5" rgba="1 0 0 1"/>
</body>
```

![[Screenshot from 2024-04-24 11-24-48.png]]

---
## 创建连杆二

第二段连杆与第一段的创建格式相同，注意其位姿定义相对于第一段连杆的刚体坐标系而非世界坐标系

```xml
<body pos="0 0 1" euler="0 0 0">
  <joint type="hinge" axis="-1 0 0" pos="0 0 -0.5"/>
  <geom type="cylinder" size="0.05 0.5" rgba="0 0.9 0 1"/>
</body>
```

![[Screenshot from 2024-04-24 11-26-54.png]]

---
## 创建末端球体

