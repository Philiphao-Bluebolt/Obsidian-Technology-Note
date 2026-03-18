+ Wikipedia - [Linear Algebra](https://en.wikipedia.org/wiki/Linear_algebra)

线性代数是研究线性映射、向量空间以及矩阵理论的数学分支，其最初的研究对象是线性方程组的求解方法。线性代数与解析几何等数学分支有着密切关系，也是控制论、机器人学、机器学习、计算机视觉、机器视觉、电路分析等工程学科的理论基础与计算工具。

线性代数的理解方式有两种，传统的教材以矩阵与线性方程组为中心，重视算子轻视本质；以《Linear Algebra Done Right》为代表的新式教材则从线性映射和向量空间角度切入，我认为更有助于学生理解线性代数的本质。

+ **学习资料**
	+ ✔️ **[Linear Algebra](https://www.youtube.com/watch?v=ZK3O402wf1c&list=PL49CF3715CB9EF31D)** - Gilbert Strang (MIT)
	+ 🪞 **[Linear Algebra Done Right](https://linear.axler.net/LADR4e.pdf)** - Sheldon Axler (SFSU) - [学习笔记](!✔️%20LADR%20学习笔记.md)
+ **编程工具**
	+ C++ Eigen
	+ Python Numpy
	+ MATLAB


---
## 学习路线

+ **Path 1 - 矩阵与方程**
	+ **行列式** - 计算 · 性质 · 展开 
	+ **矩阵** - 类型 · 运算 ( 逆矩阵 ) · 初等变换 · 秩 · 分块 · 方程组 ( 克拉默法则 · 求解 )
	+ **向量** - 性质 · 运算 · 线性组合 · 向量空间
	+ **特征值** - 求解 · 相似矩阵 · 对角化 ( Jordan型 ) · 二次型 ( 标准化 · 正定 )
	+ **线性空间** - 维数 · 基 · 线性变换 ( 矩阵形式 )
	
+ **Path 2 - 算子与空间**
	+ **** -
	+ **** -



---
## 矩阵含义 Matrix Representation

在线性代数领域，矩阵通常用于表示线性映射（Linear Mapping）或方程组；以此为基础，矩阵在其他学科可以表示万千事物

+ **线性映射** - 大小$m\times n$的矩阵可以通过右乘将一个$n$维列向量映射到一个$m$维列向量，也可以通过左乘将以一个$m$维行向量映射到一个$m$维行向量

$$\begin{bmatrix}3 & 7 &-2\\8&-1&5\end{bmatrix}\begin{bmatrix}4\\-2\\6\end{bmatrix}=\begin{bmatrix}-14\\64\\\end{bmatrix}$$$$\begin{bmatrix}-7&5\end{bmatrix}\begin{bmatrix}3 & 7 &-2\\8&-1&5\end{bmatrix}=\begin{bmatrix}19&-54&39\end{bmatrix}$$

+ **线性方程组** - 矩阵右乘的向量可以表示未知数

$$\begin{cases}3x_1+7x_2-2x_3=-14\\8x_1-x_2+5x_3=64\end{cases}\quad\to \quad \begin{bmatrix}3 & 7 &-2\\8&-1&5\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\end{bmatrix}=\begin{bmatrix}-14\\64\\\end{bmatrix}$$

+ **坐标变换** - 在解析几何和机器人学领域，矩阵可以表示坐标系的旋转和齐次变换

+ **二维张量** - 矩阵是二维的张量（Tensor）

+ **二维数据容器** - 计算机领域的二维数据（如图像）以二维矩阵的形式储存，也可以用矩阵运算进行处理
