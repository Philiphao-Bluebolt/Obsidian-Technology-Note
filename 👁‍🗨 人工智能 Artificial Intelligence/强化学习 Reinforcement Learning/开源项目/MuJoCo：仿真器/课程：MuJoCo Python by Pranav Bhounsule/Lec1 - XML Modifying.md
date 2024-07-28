+ 课程链接：[MuJoCoPy Lec1: Modifying XML file and viewing them](https://www.youtube.com/watch?v=WJa-FeFRl3Q&ab_channel=PranavBhounsule)
+ 盒子例程：[Overview Examples](https://mujoco.readthedocs.io/en/stable/overview.html#examples)
+ XML文档：[XML Reference](https://mujoco.readthedocs.io/en/stable/XMLreference.html)

MuJoCo使用XML文件描述其仿真环境，在官网文档里可以找到一个盒子的例程，本节课程的主要内容就是修改这个例程，熟悉XML文件的格式和标签

```xml
<mujoco>
  <worldbody>
    <light diffuse=".5 .5 .5" pos="0 0 3" dir="0 0 -1"/>
    <geom type="plane" size="1 1 0.1" rgba=".9 0 0 1"/>
    <body pos="0 0 1">
      <joint type="free"/>
      <geom type="box" size=".1 .2 .3" rgba="0 .9 0 1"/>
    </body>
  </worldbody>
</mujoco>
```

![[Pasted image 20240423154223.png]]

---
## 颜色对调

如果想让平面变成绿色，盒子变成红色，可以修改`rgba`属性，四个变量分别代表归一化的R、G、B、A（透明度）

```xml
...
	<geom type="plane" size="1 1 0.1" rgba="0 .9 0 1"/>
...
	  <geom type="box" size=".1 .2 .3" rgba=".9 0 0 1"/>
...
```

+ 修改后的代码：

```xml
<mujoco>
  <worldbody>
    <light diffuse=".5 .5 .5" pos="0 0 3" dir="0 0 -1"/>
    <geom type="plane" size="1 1 0.1" rgba="0 .9 0 1"/>
    <body pos="0 0 1">
      <joint type="free"/>
      <geom type="box" size=".1 .2 .3" rgba=".9 0 0 1"/>
    </body>
  </worldbody>
</mujoco>
```

![[Screenshot from 2024-04-23 16-39-07.png]]

---
## 创建新的蓝色盒子

现在，在原来的盒子上方再新增一个蓝色盒子

仿照原来的盒子的`<body>`的格式，在`<worldbody>`标签下再写（复制）一个`<body>`，修改位置和颜色

```xml
	<body pos="0 0 2">
	  <joint type="free"/>
	  <geom type="box" size=".1 .2 .3" rgba=".9 0 0 1"/>
	</body>
```

+ 修改后的代码：

```xml
<mujoco>
  <worldbody>
    <light diffuse=".5 .5 .5" pos="0 0 3" dir="0 0 -1"/>
    <geom type="plane" size="1 1 0.1" rgba="0 .9 0 1"/>
    <body pos="0 0 1">
      <joint type="free"/>
      <geom type="box" size=".1 .2 .3" rgba=".9 0 0 1"/>
    </body>
    <body pos="0 0 2">
      <joint type="free"/>
      <geom type="box" size=".1 .2 .3" rgba="0 0 .9 1"/>
    </body>
  </worldbody>
</mujoco>
```

![[Screenshot from 2024-04-24 10-14-43.png]]

---
## 关闭重力

MuJoCo的环境默认是有重力的，可以通过`<option>`标签关闭

在`<mujoco>`标签下创建一个`<option>`标签，将重力属性`gravity`置零

```xml
<option gravity="0 0 0" />
```

+ 修改后的代码：

```xml
<mujoco>
  <option gravity="0 0 0" />
  <worldbody>
    <light diffuse=".5 .5 .5" pos="0 0 3" dir="0 0 -1"/>
    <geom type="plane" size="1 1 0.1" rgba="0 .9 0 1"/>
    <body pos="0 0 1">
      <joint type="free"/>
      <geom type="box" size=".1 .2 .3" rgba=".9 0 0 1"/>
    </body>
    <body pos="0 0 2">
      <joint type="free"/>
      <geom type="box" size=".1 .2 .3" rgba="0 0 .9 1"/>
    </body>
  </worldbody>
</mujoco>
```

---
## 将蓝色盒子放平

现在，我们要将蓝色盒子较大的面朝下

蓝色盒子是直接放置在世界里的刚体，它的刚体位姿由世界坐标系描述，通过选择“渲染-坐标系-世界坐标系“，我们可以看到世界坐标系的朝向

![[Screenshot from 2024-04-24 10-36-06.png]]

可以看到，将蓝色盒子绕Y轴旋转90°即可放平，这里需要增加一个欧拉角属性`euler `

```xml
<body pos="0 0 2" euler="0 90 0">
...
```

+ 修改后的代码：

```xml
<mujoco>
  <option gravity="0 0 0" />
  <worldbody>
    <light diffuse=".5 .5 .5" pos="0 0 3" dir="0 0 -1"/>
    <geom type="plane" size="1 1 0.1" rgba="0 .9 0 1"/>
    <body pos="0 0 1">
      <joint type="free"/>
      <geom type="box" size=".1 .2 .3" rgba=".9 0 0 1"/>
    </body>
    <body pos="0 0 2" euler="0 90 0">
      <joint type="free"/>
      <geom type="box" size=".1 .2 .3" rgba="0 0 .9 1"/>
    </body>
  </worldbody>
</mujoco>
```

![[Screenshot from 2024-04-24 10-39-40.png]]

---
## 创建一个球

现在要新建一个球体

球体几何体类型标签`type`使用`sphere`，`size`属性只有一个值（半径），我们把颜色设置成银灰色

```xml
    <body pos="0 0 2">
      <joint type="free"/>
      <geom type="sphere" size=".1" rgba="0.7 0.7 0.7 1"/>
    </body>
```

+ 修改后的代码：

```xml
<mujoco>
  <worldbody>
    <light diffuse=".5 .5 .5" pos="0 0 3" dir="0 0 -1"/>
    <geom type="plane" size="1 1 0.1" rgba="0 .9 0 1"/>
    <body pos="0 0 1">
      <joint type="free"/>
      <geom type="box" size=".1 .2 .3" rgba=".9 0 0 1"/>
    </body>
    <body pos="0 0 1.5" euler="0 90 0">
      <joint type="free"/>
      <geom type="box" size=".1 .2 .3" rgba="0.1 0.8 .9 1"/>
    </body>
    <body pos="0 0 2">
      <joint type="free"/>
      <geom type="sphere" size=".1" rgba="0.7 0.7 0.7 1"/>
    </body>
  </worldbody>
</mujoco>
```

我们把重力打开，就能观察到小球下落了

![[Screenshot from 2024-04-24 10-49-06.png]]