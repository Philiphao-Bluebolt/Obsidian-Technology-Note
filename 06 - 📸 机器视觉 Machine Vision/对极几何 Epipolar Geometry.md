对极几何描述了一个空间3D点与它被不同位置相机所捕捉的2D成像点之间的几何约束关系，是双目视觉和三维重建等技术的数学理论基础。

+ [基本概念](#基本概念)
+ [针孔相机模型](#针孔相机模型)

---
## 基本概念

在三维空间中有一点$P$和两个不同位姿的针孔相机$O_r$、$O_l$，点$P$在两个相机成像面上的投影点分别为$p_l$、$p_r$。由于拍照过程中光沿直线传播，投影点$p_l$、$p_r$分别位于直线$O_lP$和$O_rP$上，因此容易发现$P$、$O_l$、$O_r$、$p_l$、$p_r$**五点共面**于平面$O_lO_rP$。

平面$O_lO_rP$称为**对极面**；两个相机中心点的连线$O_lO_r$也位于对极面上，称为**基线**；基线$O_lO_r$与两个相机成像平面分别相交，两个交点$e_l$、$e_r$被称为**对极点**；每个对极点与同一个成像面上的投影点的连线$e_lp_l$、$e_rp_r$称为**对极线**，这两条对极线同时也是成像平面和对极面的交线。

> **对极面（Epipolar Plane）**：由三维点$P$和两个相机中心点$O_l,O_r$确定的平面
> **基线（Base Line）**：两个相机中心点$O_l$、$O_r$的连线，位于对极面上
> **对极点（Epipole）**：有两个，分别是基线与两个相机成像平面的交点
> **对极线（Epipolar Line）**：对极平面与成像平面的交线


---
## 针孔相机模型

这里补充一下针孔相机模型的定义，参见[Sensors](Sensors.md)





---
## 深度估计

对极几何理论最常见的用途是深度估计，也就是在已知两个相机的相对位姿、参数、以及两张图像的情况下推导出三维点与相机的距离。







---
## 参考

+ 视频
	+ [Epipolar Geometry Uncalibrated Stereo](https://www.youtube.com/watch?v=6kpBqfgSPRc&ab_channel=FirstPrinciplesofComputerVision)