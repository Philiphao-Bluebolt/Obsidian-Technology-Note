+ 官方文档：[http://wiki.ros.org/geometry_msgs](http://wiki.ros.org/geometry_msgs)

`geometry_msgs`提供了与机器人相关的几何消息类型。

+ 基本几何消息有十种，分别是`Accel`（加速度）、`Inertia`（）、`Point`（点）、`Polygon`、`Pose`（位姿）、`Quaternion`（四元数）、`Transform`（刚体变换）、`Twist`（速度旋量）、`Vector3`（三维向量）、`Wrench`（力旋量），其余是衍生的消息。

不少消息类型都有带方差版本`..WithCovariance`和带戳（`Header`）版本`..Stamped`

+ 带方差版本`..WithCovariance`包含一个6x6的方差矩阵，反映数据的不确定性（置信度）
+ 带戳版本`..Stamped`含有一个`Header`消息类型，用于储存消息的编号、时间以及所在的坐标系ID

强烈推荐**使用带戳（`Header`）版本**的几何消息，坐标系ID可以为TF坐标变换工具提供正确的坐标系信息，时间戳则可以用于时间同步。

---
## `TransformStamped`：刚体变换（含Header和子坐标系）

`geometry_msgs/TransformStamped`用一个三维向量`translation`和一个四元数`rotation`描述刚体变换，从`frame_id`变换到`child_frame_id`坐标系，用于`TF`坐标变换工具。

```msg
std_msgs/Header header
  uint32 seq
  time stamp
  string frame_id
string child_frame_id
geometry_msgs/Transform transform
  geometry_msgs/Vector3 translation
    float64 x
    float64 y
    float64 z
  geometry_msgs/Quaternion rotation
    float64 x
    float64 y
    float64 z
    float64 w
```

无`Header`版本为`geometry_msgs/Transform`

---

