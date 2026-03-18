PlotJuggler支持话题数据实时分析、日志分析，被认为是ROS环境下最好用的数据绘图工具

[[#安装配置]]
[[#话题消息实时绘图]]
[[#日志分析]]
[[#ROSbag话题分析]]
[[#不存在的点]]

---
## 安装配置

由于ROS安装包默认**不包含**PlotJuggler，使用前需要另外安装

+ 安装命令：（Noetic是ROS发行版本）

注意一定要加最后面的`-ros`，否则无法实时分析话题数据

```bash
sudo  apt  install  ros-noetic-plotjuggler-ros
```

+ 打开命令：

```bash
rosrun  plotjuggler  plotjuggler
```

成功打开后，~~会弹出来一张模因图~~，界面如下图所示。

![[Pasted image 20240323135415.png]]

一定要确认左上角的信息流（Streaming）有“ROS话题订阅者”的选项，否则无法实时分析话题。

---
## 话题消息实时绘图

左上角的“Streaming”选择“ROS Topic Subscriber”，点击开始，在弹出的窗口里选择需要监听的话题通道，然后在左下角的时间序列“Timeseries List”把需要看的通道拖到右侧图窗中即可实现数据的在线绘图。

![[Pasted image 20240323135528.png]]

+ 暂停/继续监听：左上角“Streaming”的暂停按钮；

+ 关闭/显示曲线：点击图窗上的对应图例；

+ 多图窗分屏：图窗区域右键选择水平分屏（Split Horizontally）、垂直分屏（Split Vertically）

![[Pasted image 20240323135616.png]]

---
## 日志分析

+ PX4飞控日志分析教程：[https://docs.px4.io/main/en/log/plotjuggler_log_analysis.html](https://docs.px4.io/main/en/log/plotjuggler_log_analysis.html)

这里以飞控日志为例。在QGC中导出的飞控日志文件可以直接拖进PlotJuggler里，弹出的窗口会显示日志的总览、飞控参数和显示消息；其余数据在“Timeseries List”列表中，可以拖到图窗中分析。

![[Pasted image 20240323135719.png]]

飞控日志数据的具体含义参考PX4内部传输协议uORB。

+ PX4中间层uORB文档：[https://docs.px4.io/main/en/middleware/](https://docs.px4.io/main/en/middleware/)

![[Pasted image 20240323135744.png]]

---
## ROSbag话题分析

参见[[ROSbag：话题录制#图表分析]]

---
## 不存在的点

要注意，PlotJuggler绘图时会把相邻的数据点用直线相连，但有些时间段实际是没有数据点的。下图是Offboard模式下的速度控制点，中间的三段直线是没有发布控制点的

![[Pasted image 20240326152352.png]]