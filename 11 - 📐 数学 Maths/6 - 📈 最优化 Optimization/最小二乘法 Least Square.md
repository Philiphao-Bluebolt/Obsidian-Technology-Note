+ Wikipedia - [Least squares](https://en.wikipedia.org/wiki/Least_squares)

最小二乘法是一类用于数据拟合的代数方法，其基本思想是最小化样本拟合误差的平方和

+ [[#线性模型 Linear Model]]
	+ 

---
## 线性模型 Linear Model

+ **公式**：$x=(A^TA)^{−1}A^T b$

线性最小二乘问题的基本框架是拟合问题：对于一组N维数据点，求一个最优超平面（高维平面），使数据点的**拟合误差平方和最小**

要注意的是，数据点的拟合误差**并不是**数据点到超平面的垂直距离，而是因变量方向上与估计点的距离（与之相对，最优分类问题则考虑垂直距离）

> [!NOTE] 举例：二维数据点拟合
> 某次实验中采集到5个二维数据点$(x_1,y_1),(x_2,y_2)...(x_5, y_5)$，尝试找出一条直线$y=k_1x+k_2$拟合这些数据点的变化趋势。
> $$\begin{cases}y_1=k_1x_1+k_2\\y_2=k_1x_2+k_2\\\quad\quad\vdots\\y_5=k_1x_5+k_2\end{cases}$$
> 由于该方程组属于方程多于未知数的超定义（Overdefined）方程，实际上是无解的，因此不可能找到一条直线可以精确穿过所有数据点。退而求其次，尝试找一条使**拟合误差平方和最小**的最优直线。
> 
> 将齐次方程组写成矩阵形式：
>$$\begin{bmatrix}x_1&1\\x_2&1\\\vdots&\vdots\\x_5&1\end{bmatrix}\begin{bmatrix}k_1\\k_2\end{bmatrix}=\begin{bmatrix}y_1\\y_2\\\vdots\\y_5\end{bmatrix}$$
> 等式右边是每个数据点因变量的真实取值组成的向量$\begin{bmatrix}y_1&y_2&\cdots&y_5\end{bmatrix}^T$，等式左边计算的结果则是待求直线$y=k_1x+k_2$对这些数据点的预测结果组成的向量$\begin{bmatrix}\hat{y}_1&\hat{y}_2&\cdots&\hat{y}_5\end{bmatrix}^T$
> 
> 这样，拟合误差的平方和就可以表示成两边向量的欧氏距离$||y-\hat{y}||^2$

### 代数抽象

上述数据最优拟合问题可以抽象成一般形式的线性最小二乘问题

> [!NOTE] 线性最小二乘问题
> 对于齐次线性方程组$Ax=b$，求向量$x$，使得等式左右两边向量的距离最小
> $$\min_x ||Ax-b||^2$$







### 几何角度

