+ 官方文档：[https://wiki.ros.org/rosbag](https://wiki.ros.org/rosbag)

ROSbag是一个命令行话题录制工具，它可以记录指定话题的数据，以`.bag`文件的形式保存数据用于后期的分析以及环境重现。

ROSbag的回放分析可以使用[[Rqt Bag：播放、查看录包]]工具。

---
## 录制

+ 开始录制全部活跃话题：

```bash
rosbag  record  -a
```

若不指定保存数据文件的名称和位置，默认以`年-月-日-时-分-秒.bag`的名称保存在命令执行路径中。

+ 仅录制话题`/mavros/local_position/odom`，保存在`~/bag`文件夹，命名为`test_1_rosbag.bag`：

```bash
rosbag  record  -o  ~/bag/test_1_rosbag.bag  /mavros/local_position/odom
```

如果录制数据量很大的话题（如点云、图像通道），几分钟的录制所产生的录制文件可能已经有几个G的大小。

---
## 图表分析

保存的`.bag`文件可以直接拉到PlotJuggler进行图表分析

![[Pasted image 20240316175820.png]]

---
## 重现

ROSbag可以将录制的话题重新“播放”到ROS系统中，此时用`rostopic list`中可以看到当时录制的话题，`rostopic echo`还能监听到话题的消息。

```bash
rosbag  play  test_1.bag
```

![[Pasted image 20240316175929.png]]

---
## 提取部分话题

可以在已有的`.bag`文件中提取出指定的部分话题，保存为一个新的`.bag`文件

```bash
rosbag  filter  input.bag  output.bag  "topic == '/mavros/state' or topic == '/rosout'"
```

---
## 修复

如果`rosbag`的录制没有正确停止（比如说强制关机） ，输出文件会停留在活跃状态，文件后缀显示`.bag.active`，这样的文件即使删去`.active`后缀，用PlotJuggler打开时会提示No Index，无法分析。

修复方法：

1. 重命名去掉后缀`.active` 
2. 运行下面的指令

```bash
rosbag reindex test_1.bag
```

修复完成后会出现一个`.bag`文件，就可以用于分析了。原本的文件后缀会变成`.origin.bag`