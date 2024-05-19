这里收录我使用MuJoCo过程中遇到的问题解决方案

---
## 修改或关闭重力

修改整个仿真环境中的重力可以通过修改`<option>`标签的`gravity`属性实现

+ 重力更改为朝向x轴正方向

```xml
<option gravity="9.81 0 0">
```

+ 赋值为`0 0 0`关闭重力

```xml
<option gravity="0 0 0">
```

### 关闭特定物体的重力

+ 文档：[mjData](https://mujoco.readthedocs.io/en/stable/APIreference/APItypes.html#mjdata)

![[Pasted image 20240501225614.png]]

有时候，我们只希望某仿真环境中的某个物体不受重力，使其可以悬浮在半空中，但是MuJoCo并不支持移除单一物体的重力。容易想到的是，对物体施加一个竖直向上的力与重力相抵消

```python
# 对2号刚体施加沿z轴正方向的力
self.mjdata.xfrc_applied[2, 2] = self.model.body_mass[2] * 9.81
```


---
## 使刚体变光滑

刚体下属`<geom>`标签的`friction`属性可以修改刚体上对应几何体的光滑度，当两个光滑物体相接触时，摩擦力不起作用

`friction`属性的三个值分别指滑动摩擦、扭转摩擦和滚动摩擦（单位？）

```xml
<geom type="plane" size="10 10 0.1" friction="0 0 0"/>
```

---
## 引入绳系约束

+ 文档：[tendon](https://mujoco.readthedocs.io/en/stable/XMLreference.html#tendon)

绳系约束可以通过`<tendon>`实现，

---
## 读取、修改刚体的位置与速度

+ 文档：[mjData](https://mujoco.readthedocs.io/en/stable/APIreference/APItypes.html#mjdata)

![[Pasted image 20240501172506.png]]

这里使用到API程序接口`mjData`类的成员`qpos`和`qvel`，这两个数组分别存放仿真模型中所有刚体的位姿（Pose）和速度旋量（Twist），不包括世界刚体`<worldbody>`

### 储存格式：

+ 刚体位姿`qpos`：每七个位置存放一个刚体的位置坐标`xyz`+姿态四元数`wxyz`
+ 刚体速度`qvel`：每六个位置存放一个刚体的线性速度`xyz`+角速度

```python
model = mujoco.MjModel.from_xml_path(modelName)
data = mujoco.MjData(model)

data.qpos[0] #第一个刚体的x坐标
data.qpos[3] #第一个刚体的z坐标

data.qpos[12] #第二个刚体的姿态四元数y

data.qvel[5] #第一个刚体的yaw欧拉角
```

不知道有没有办法按刚体名字访问，不然刚体多起来就麻烦了

---
## 程序重置模型

Python接口`mujoco`似乎并没有提供重置整个仿真模型的参数，只能用逐个重新设置`qpos`和`qvel`的方法来还原每个刚体的状态

---
## 获取刚体质量

+ 文档：[mjModel](https://mujoco.readthedocs.io/en/stable/APIreference/APItypes.html#mjmodel)

![[Pasted image 20240501174053.png]]

刚体的质量可以通过`mjModel`的`body_mass`数组获取，数组包括世界刚体`<worldbody>`的质量（一般为0）

---
## 检测碰撞

+ 文档：[mjData](https://mujoco.readthedocs.io/en/stable/APIreference/APItypes.html#mjdata)、[mjContact](https://mujoco.readthedocs.io/en/stable/APIreference/APItypes.html#mjcontact)

![[Pasted image 20240502210412.png]]

`mjData`有一个成员`contact`专门用于输出仿真器检测到的碰撞，以列表的形式输出所有的碰撞，每个碰撞的信息都存储在对象`mjContact`中

---
## 创建纯视觉标记

+ 


