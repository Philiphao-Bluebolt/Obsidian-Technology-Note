+ PX4文档：[Using Vision or Motion Capture Systems for Position Estimation](https://docs.px4.io/main/en/ros/external_position_estimation.html)

PX4支持使用飞控外部的传感器进行位置估计（Position Estimation），常见的位置估计传感器包括深度相机（视觉里程计）和三维动捕系统。

---
## EKF2估算器

EKF2（EKF指扩展卡尔曼滤波，Extended Kalman Filter）是PX4内部的位置估算器，


PX4要求飞机必须