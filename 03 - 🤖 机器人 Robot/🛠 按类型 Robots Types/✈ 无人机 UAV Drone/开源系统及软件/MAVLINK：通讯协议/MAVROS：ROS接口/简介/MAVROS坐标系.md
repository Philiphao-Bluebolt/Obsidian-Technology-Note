+ 详见：[[参考：无人机常用坐标系]]

MAVROS启动后会建立六个坐标系，其中`map_ned`、`odom_ned`、`base_link_frd`是为了把MAVROS坐标惯例转换为PX4坐标惯例

+ `map`：世界坐标系或称本地坐标系，原点位于无人机上电处，坐标轴方向在MAVROS使用ENU惯例，在PX4中使用NED惯例
+ `odom`：里程计坐标系，外部测量的里程计数据使用的坐标系
+ `base_link`：机体坐标系，原点位于飞控模块中心，坐标轴方向在MAVROS使用FLU惯例，在PX4使用FRD惯例

![[Screenshot from 2024-05-20 14-42-22.png]]

---
## 相关讨论

[TF Tree confusion. How to configure to ROS REP 105](https://github.com/mavlink/mavros/issues/1388)

