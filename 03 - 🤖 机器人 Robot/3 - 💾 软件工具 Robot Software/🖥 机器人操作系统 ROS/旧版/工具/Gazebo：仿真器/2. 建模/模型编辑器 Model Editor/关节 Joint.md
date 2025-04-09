关节描述了模型各连杆之间的运动约束，是机器人模型的重要元素。Gazebo中的关节构建类似DH参数法：[[3.9 DH参数法]]，需要建立一个关节坐标系。

![[Screenshot from 2024-04-11 14-47-56.png]]

在模型编辑器中点击这个图标可以创建关节，关节设置的部分参数（如关节限位）只能在创建关节以后再通过关节检视器（Joint Inspector）修改

![[Screenshot from 2024-04-11 10-40-24.png]]

Gazebo中的关节在SDF文件中的标签为`<joint>`，有八种类型：

+ [[#固定 Fixed]]
+ [[#转动 Revolute]]
+ 双转动 Revolute2
+ 平移 Prismatic
+ 螺旋 Screw
+ 万向 Universal
+ [[#球关节 Ball]]
+ 齿轮约束 Gearbox

---
## 固定 Fixed

+ 自由度：0
+ 效果：子连杆在关节坐标系的位置固定

固定关节不具有任何自由度，本质上就是将两个连杆铆接在一起，使其相对位姿不再发生改变，因此关节坐标系的位置不影响固定关节的作用效果

---
## 转动 Revolute

+ 自由度：1（旋转）
+ 效果：子连杆可以绕关节坐标系的转轴向量（向量起始点在关节坐标系原点）旋转

转动关节就是常见的转动副，只允许子连杆相对于关节坐标系中指定的转轴向量旋转，不允许平移或绕其他方向旋转

转轴向量由黄色箭头表示

---
## 球关节 Ball

+ 自由度：3（三旋转）
+ 效果：子连杆可以绕关节坐标系的原点自由旋转，但不能靠近或远离原点

球关节

---



---
## 参考资料

+ 关节Revolute2和Universal的不同：[Revolute2 vs Universal joint?](https://answers.gazebosim.org//question/26373/revolute2-vs-universal-joint/)

+ 关节示例模型下载：[Demo Joint Type](https://app.gazebosim.org/OpenRobotics/fuel/models/Demo%20Joint%20Types)
