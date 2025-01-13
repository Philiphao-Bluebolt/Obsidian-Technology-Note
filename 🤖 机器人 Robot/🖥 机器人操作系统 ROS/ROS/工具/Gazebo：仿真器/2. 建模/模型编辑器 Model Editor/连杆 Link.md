连杆是组成模型的刚体，在SDF文件中的标签是`<link>`，是模型标签`<model>`的子标签

在模型编辑器中通过左侧栏插入连杆，有三种类型可供选择

1. 简单形状（Simple Shapes）：圆柱、球形、长方体；这三种基本几何形状可以修改尺寸

![[Screenshot from 2024-04-10 14-55-27.png]]

2. 自定义形状（Custom Shapes）：通过导入其他建模软件导出的3D Mesh文件生成连杆模型，支持的文件类型有[.dae](https://en.wikipedia.org/wiki/COLLADA)、[.stl]()、.obj

![[Screenshot from 2024-04-10 15-17-37.png]]

3. 导入已有模型（Model Database） ：导入本地保存的模型SDF文件生成连杆

![[Screenshot from 2024-04-10 14-55-51.png]]

插入连杆后，右键打开连杆检视器（Link Inspector）可以修改连杆的属性，连杆的属性有三部分：

+ [[#基本属性 Link]]
+ [[#可视体 Visual]]
+ [[#碰撞体 Collision]]

---
## 基本属性 Link

基本属性包括连杆的基本物理性质、位姿等属性，在SDF文件中，这一类属性的标签（如`<pose>`、`<gravity>`）直接就是连杆标签`<link>`的子标签

| 英文名                     | 中文解释     | SDF文件标签                                         | 标签级别 | 默认值               | 描述                                                     |
| ----------------------- | -------- | ----------------------------------------------- | ---- | ----------------- | ------------------------------------------------------ |
| Self Collide            | 启用自碰撞    | `<self_collide>`                                | 4    | 0                 | 启用后，与同一模型中其它连杆会发生碰撞；两个连杆只需有一个启用自碰撞                     |
| Gravity                 | 启用重力     | `<gravity>`                                     | 4    | 1                 | 关闭后，连杆不受重力影响                                           |
| Kinematic               | 启用运动学模式  | `<kinematic>`                                   | 4    | 0                 | 启用后，连杆不再受物理仿真中的力的影响，只能通过ROS服务改变位姿和速度；常用来构建固定连杆         |
| Density                 | 密度       | /（不存）                                           | 4    | ~                 | 改变密度的同时会改变连杆的质量，注意这个属性没有保存在SDF文件中，这是因为通过体积和质量可以计算出密度   |
| Inertial                | 惯性       | `<inertial>`                                    | 4    | ~                 | 质量、位姿、惯性张量的父标签                                         |
| Mass                    | 质量       | `<mass>`                                        | 5    | ~                 | 连杆的质量                                                  |
| Pose                    | 惯性坐标系位姿  | `<pose>`                                        | 5    | 0 0 0 0 0 0       | 惯性坐标系相对连杆坐标系的位姿，其原点是连杆的质心，三轴方向则决定惯性张量的实际意义             |
| Inertia                 | 惯性张量     | `<inertia>`                                     | 5    | ~                 | 惯性张量决定了旋转运动的行为                                         |
| Ixx、Ixy、Ixz、Iyy、Iyz、Izz | 惯性张量矩阵取值 | `<ixx>`、`<ixy>`、`<ixz>`、`<iyy>`、`<iyz>`、`<izz>` | 6    | ~                 | 惯性张量矩阵的具体取值                                            |
| Pose                    | 连杆位姿     | `<pose>`                                        | 4    | \~ \~ \~ \~ \~ \~ | 连杆坐标系相对于模型坐标系的位姿；在编辑器创建模型时，相对于世界坐标系；编辑模型时，相对于原位置的模型坐标系 |
| Enable Wind             | 启用风的影响   | `<enable_wind>`                                 | 4    | 0                 | 启用后，模型的运动会受到风力的影响                                      |
| Wind                    | 风        | `<wind>`                                        | 4    | 0 0 0             | 三维向量，指定模型所受风力的方向，这个设置会覆盖掉世界风的影响                        |

---
## 可视体 Visual

可视体描述模型的视觉渲染效果，它的SDF标签`<visual>`是连杆标签`<link>`的子标签

| 英文名          | 中文解释  | SDF文件标签          | 标签级别 | 默认值         | 描述                                        |
| ------------ | ----- | ---------------- | ---- | ----------- | ----------------------------------------- |
| Cast shadows | 启用影子  | `<cast_shadows>` | 5    | 1           | 开启后会渲染出模型的影子                              |
| Transparency | 透明度   | `<transparency>` | 5    | 0           | 取值范围0~1，0表示不透明，1表示完全透明（隐形）                |
| Laser retro  |       |                  |      |             |                                           |
| Pose         | 可视体位姿 | `<pose>`         | 5    | 0 0 0 0 0 0 | 可视体坐标系相对于连杆坐标系的位姿                         |
| Geometry     | 几何形状  | `<geometry>`     | 5    | ~           | 可视体的几何形状，选项有长方体、圆柱、球形、网格模型（Mesh）、Polyline |
| Material     | 材质    | `<material>`     | 5    |             |                                           |
| Script       |       | `<script>`       | 6    |             |                                           |
| Shader type  |       | `<shader>`       | 6    |             |                                           |
| Normal map   |       | `<normal_map>`   | 7    |             |                                           |
| Ambient      |       | `<ambient>`      | 6    |             |                                           |
| Diffuse      |       | `<diffuse>`      | 6    |             |                                           |
| Specular     |       | `<specular>`     | 6    |             |                                           |
| Emissive     |       | `<emissive>`     | 6    |             |                                           |
| Lighting     |       | `<lighting>`     | 6    |             |                                           |
| Meta         |       | `<meta>`         | 5    |             |                                           |
| Layer        |       | `<layer>`        | 6    |             |                                           |


---
## 碰撞体 Collision

碰撞体的参数决定了模型与物理环境的互动行为，类似3D游戏中的“碰撞箱”，它的SDF标签`<collision>`是`<link>`的子标签

| 英文名                             | 中文解释 | SDF文件标签 | 标签级别 | 默认值 | 描述  |
| ------------------------------- | ---- | ------- | ---- | --- | --- |
| Laser retro                     |      |         | 5    |     |     |
| Max contacts                    |      |         | 5    |     |     |
| Pose                            |      |         | 5    |     |     |
| Geometry                        |      |         | 5    |     |     |
| Surface                         |      |         | 5    |     |     |
| Friction                        |      |         | 6    |     |     |
| Mu                              |      |         | 8    |     |     |
| Mu2                             |      |         | 8    |     |     |
| Fdir1                           |      |         | 8    |     |     |
| Slip1                           |      |         | 8    |     |     |
| Slip2                           |      |         | 8    |     |     |
| Torsional                       |      |         | 7    |     |     |
| Coefficient                     |      |         | 8    |     |     |
| Use patch radius                |      |         | 8    |     |     |
| Patch radius                    |      |         | 8    |     |     |
| Surface radius                  |      |         | 8    |     |     |
| Ode                             |      |         | 8    |     |     |
| Slip                            |      |         | 9    |     |     |
| Restitution coefficient         |      |         |      |     |     |
| Bounce threshold                |      |         |      |     |     |
| Soft cfm                        |      |         |      |     |     |
| Soft erp                        |      |         |      |     |     |
| Kp                              |      |         |      |     |     |
| Kd                              |      |         |      |     |     |
| Max vel                         |      |         |      |     |     |
| Min depth                       |      |         |      |     |     |
| Collide without contact         |      |         |      |     |     |
| Collide without contact bitmask |      |         |      |     |     |
| Collide bitmask                 |      |         |      |     |     |
| Elastic modulus                 |      |         |      |     |     |
