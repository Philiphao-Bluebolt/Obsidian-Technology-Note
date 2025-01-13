+ 官方文档：[https://wiki.ros.org/rqt](https://wiki.ros.org/rqt)

Rqt是ROS自带的基于Qt图形交互界面开发的多功能数据可视化工具，它包含了许多常用的调试插件（Plugin），这些插件可以在Rqt主界面中打开，也可以使用命令单独打开。

---
## Rqt主界面

```bash
rqt
```

在Rqt的主页面中，不同的插件可以放置在同一个窗口中，用户可以自定义一个综合的开发调试工具。

![[Pasted image 20240323133734.png]]

---
## Rqt完整插件工具

+ Container 窗口容器
+ Actions 
	+ Action Type Browser
+ Configuration 配置
	+ Dynamic Reconfigure
	+ Launch
+ Introspection 自检
	+ Node Graph：[[Rqt Graph：节点话题可视化]]
	+ Package Graph
	+ Process Monitor
+ Logging 日志
	+ Bag：[[Rqt Bag：播放、查看录包]]
	+ Console
	+ Logger Level
+ Miscellaneous Tools 杂项
	+ Python Console
	+ Shell
	+ Web
+ Robot Tools 机器人
	+ Diagnostics Viewer
	+ Moveit! Monitor
	+ Robot Steering
	+ Runtime Monitor
+ Services 服务
	+ Service Caller：[[Rqt Service Caller：请求服务]]
	+ Service Type Browser
+ Topics 话题
	+ Message Publisher：[[Rqt Message Publisher：话题消息发布]]
	+ Message Type Browser
	+ Topic Monitor：[[Rqt Topic：话题监视器]]
+ Visualization 可视化
	+ Image View：[[Rqt Image View：查看话题图像]]
	+ Navigation Viewer
	+ Plot：[[Rqt Plot：话题数据实时绘图]]
	+ Pose View
	+ RViz
	+ TF Tree：[[Rqt TF Tree：查看TF坐标变换树]]