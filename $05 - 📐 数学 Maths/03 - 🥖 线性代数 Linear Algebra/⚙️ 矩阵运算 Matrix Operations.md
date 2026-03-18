+ **证明过程**：[[🧐 线代相关证明 Proofs in Linear Algreba]]
+ **矩阵分类**：[[🗃 矩阵分类 Matrix Classification]]

> [!example] 矩阵运算的类型
> + 🎯 矩阵性质（Matrix Property）
> + 🎳 逐项运算（Element-wise）
> + ✖ 乘法类运算（Multiplication Related）
> + 🪓 矩阵分解（Decomposition & Factorization）
> + 🧩 分块运算（Partition Operation）
> + 🪀 其他运算（Others）

| 类型  | 具体运算                                                                  | 符号                 | 适用   | 输出类型     |
| :-: | :-------------------------------------------------------------------- | ------------------ | ---- | -------- |
| 🎯  | [[#行列式 Determinant]]                                                  | $\det(A)$          | 仅方阵  | 标量       |
| 🎯  | [[#求逆 Inverse]]                                                       | $A^{-1}$           | 仅方阵  | 同阶方阵     |
| 🎯  | [[#伪逆 Pseudo-inverse]]                                                | $A^+$              | 任意矩阵 | 矩阵       |
| 🎯  | [[#转置 Transpose]]                                                     | $A^T$              | 任意矩阵 | 行列对换矩阵   |
| 🎯  | [[#共轭转置 Conjugate Transpose]]                                         | $A^*$              | 复矩阵  | 行列对换共轭矩阵 |
| 🎯  | [[#特征值与特征向量 Eigenvalue & Eigenvector]]                                | $\lambda_i;v_i$    | 仅方阵  | 标量、向量    |
| 🎯  | [[#秩 Rank]]                                                           | $\mathrm{rank}(A)$ | 任意矩阵 | 标量       |
| 🎯  | [[#行空间与列空间 Row and Column Space]]                                     |                    | 任意矩阵 | 线性空间     |
| 🎯  | [零空间 Nullspace / 核 Kernel](#零空间%20Nullspace%20/%20核%20Kernel)         | $\mathrm{ker}(A)$  | 任意矩阵 | 线性空间     |
| 🎯  | [[#迹 Trace]]                                                          | $\mathrm{tr}(A)$   | 仅方阵  | 标量       |
| 🎳  | [[#加减 Addition & Subtraction]]                                        | $A\pm B$           | 任意矩阵 | 同型矩阵     |
| 🎳  | [[#倍乘 Scalar Multiplication]]                                         | $k A$              | 任意矩阵 | 同型矩阵     |
| 🎳  | [[#逐项乘 Hadamard Multiplication]]                                      | $A\odot B$         | 任意矩阵 | 同型矩阵     |
|  ✖  | [[#乘法 Multiplication]]                                                | $AB$               | 任意矩阵 | 行取左列取右矩阵 |
|  ✖  | [[#乘方 Power]]                                                         | $A^k$              | 仅方阵  | 同阶方阵     |
|  ✖  | [[#初等变换 Elementary Operation]]                                        |                    | 任意矩阵 | 同型矩阵     |
|  ✖  | [[#高斯消元法 Gaussian Elimination]]                                       |                    | 任意矩阵 | 行阶梯矩阵    |
|  ✖  | [相似变换 Similarity Transformation](#相似变换%20Similarity%20Transformation) | $P^{-1}AP$         | 仅方阵  | 相似矩阵     |
|  ✖  | [[#相似对角化 Diagonalization]]                                            | $P^{-1}AP$         | 方阵   | 相似对角矩阵   |
|  ✖  | [[#若尔当标准型 Jordan Normal Form]]                                        | $P^{-1}AP$         | 方阵   | 若尔当相似标准型 |
| 🪓  | [上下三角分解 LU Decomposition](#上下三角分解%20LU%20Decomposition)               | $LU$               |      |          |
| 🪓  | [正交上三角分解 QR Decomposition](#正交上三角分解%20QR%20Decomposition)             | $QR$               |      |          |
| 🪓  | [[#奇异值分解 Singular Value Decomposition]]                               | $U\Sigma V^*$      |      | 所有复矩阵    |
| 🧩  | 分块加减 Block Addition & Subtraction                                     |                    | 任意矩阵 |          |
| 🧩  | 分块乘法 Block Multiplication                                             |                    | 任意矩阵 |          |
| 🧩  | 分块求逆 Block Inverse                                                    |                    | 仅方阵  |          |
| 🧩  | 分块行列式 Block Determinant                                               |                    | 仅方阵  |          |
| 🪀  | [[#矩阵指数 Matrix Exponential]]                                          | $e^A$              | 仅方阵  | 同阶方阵     |
| 🪀  | 矩阵对数 Matrix Logarithm                                                 |                    | 仅方阵  |          |
| 🪀  | [[#导数 Derivative]]                                                    |                    | 任意矩阵 |          |
| 🪀  | [[#积分 Integral]]                                                      |                    | 任意矩阵 |          |

+ 其他话题 Other Topics
	+ [[#矩阵运算的编程实现 Matrix Operations by Coding]]
	+ [[#矩阵与向量 Matrix & Vector]]
	+ [[#雅可比矩阵 Jacobian Matrix]]


---
## 行列式 Determinant

+ **适用于** - 方阵
+ **符号** - $\det(A)$、$|A|$

只有方阵才能求行列式
$$\det(A)=|A|=\det(\begin{bmatrix}a&b&c\\d&e&f\\g&h&i\end{bmatrix})$$
+ 二阶行列式
$$\det(\begin{bmatrix}a&b\\c&d\end{bmatrix})=ad-bc$$
+ 三阶行列式
$$\det(\begin{bmatrix}a&b&c\\d&e&f\\g&h&i\end{bmatrix})=aei+bgf+cdh-ceg-bdi-afh$$

### 高阶行列式求解 Large Determinant Solution

高阶行列式的展开式非常复杂，需要降低行列式阶数才能写出解析表达式

#### 拉普拉斯展开法 Laplace Expansion

行列式的值，等于任意一行或一列上的所有元素与自身代数余子式乘积的和
$$\det(A)=\sum_{i=1}^{n} a_{ij}A_{ij}=\sum_{j=1}^{n} a_{ij}A_{ij}$$
+ **代数余子式**$A_{ij}$：元素$a_{ij}$的代数余子式是原行列式删去$a_{ij}$所在的行和列剩下的行列式，乘以一个由所在行列决定正负的因子$(-1)^{i+j}$

$$a_{01}\begin{cases}i=1\\j=2\end{cases} \quad\to\quad A=\begin{bmatrix}\color{orange}a&\color{red}b&\color{orange}c\\\color{green}d&\color{orange}e&\color{green}f\\\color{green}g&\color{orange}h&\color{green}i\end{bmatrix} \quad\to \quad A_{01}=\begin{bmatrix}\color{green}d&\color{green}f\\\color{green}g&\color{green}i\end{bmatrix}\times(-1)^{1+2}=-\begin{bmatrix}d&f\\g&i\end{bmatrix}$$

比如说，选择第二列
$$\det(A)=\det(\begin{bmatrix}a&\color{red}b&c\\d&\color{red}e&f\\g&\color{red}h&i\end{bmatrix})=-b\begin{bmatrix}d&f\\g&i\end{bmatrix}+e\begin{bmatrix}a&c\\g&i\end{bmatrix}-h\begin{bmatrix}a&c\\d&f\end{bmatrix}$$
### 行列式的性质

+ 



---
## 求逆 Inverse

+ **适用于** - 方阵（可逆矩阵）
+ **符号** - $A^{-1}$
+ **相关概念** - 行列式、可逆矩阵、奇异矩阵

矩阵$A$的逆矩阵是一个相同阶数的矩阵
$$A^{-1}=\begin{bmatrix}1&2\\3&4\end{bmatrix}^{-1}=\begin{bmatrix}-2&1\\1.5&-0.5\end{bmatrix}$$
求逆是矩阵最重要的运算之一，矩阵等式的移项需要用到矩阵的逆
$$\begin{align}A&=B\\AB^{-1}&=I\end{align}$$
只有可逆矩阵，即行列式不为零的矩阵才能求逆；不能求逆的矩阵称为奇异矩阵（参见[[#可逆矩阵与奇异矩阵 Invertible Matrix & Singular Matrix]]）

### 逆矩阵求解

#### 伴随矩阵法 Adjugate Matrix Method

矩阵$A$的逆等于其伴随矩阵除以行列式
$$A^{-1}=\frac{adj(A)}{|A|}$$
+ **伴随矩阵**$adj(A)$：由矩阵$A$所有元素的代数余子式组成的矩阵的**转置**
$$A=\begin{bmatrix}a_{11}&a_{12}\\a_{21}&a_{22}\end{bmatrix}\quad\to\quad adj(A)=\begin{bmatrix}A_{11}&A_{12}\\A_{21}&A_{22}\end{bmatrix}^T=\begin{bmatrix}A_{11}&A_{21}\\A_{12}&A_{22}\end{bmatrix}$$

#### 初等变换法 Elementary Transform Method

将一个同阶的单位矩阵$I$并在矩阵$A$的右侧，组成一个$n\times2n$的长方形矩阵，对这个矩阵进行**行变换**
，当左侧原本的矩阵$A$变成单位矩阵$I$时，右侧原本的单位矩阵$I$就变成$A$的逆矩阵
$$\begin{bmatrix}A&I\end{bmatrix}\to\begin{bmatrix}I&A^{-1}\end{bmatrix}$$
其原理如下（矩阵$B$表示进行的所有行变换）
$$AB=I\to B=A^{-1}$$
$$IB=IA^{-1}=A^{-1}$$

### 求逆运算的性质

+ 矩阵与自身的逆相乘得到单位矩阵
$$AA^{-1}=A^{-1}A=I$$
+ 求逆会调转乘法运算顺序
$$(ABC)^{-1}=C^{-1}B^{-1}A^{-1}$$
+ 求逆与转置运算顺序可换
$$(A^{-1})^T=(A^T)^{-1}$$

---
## 伪逆 Pseudo-inverse

+ **适用于** - 所有矩阵
+ **符号** - $A^+$
+ **相关领域** - 最优化（最小二乘）、机器人学（逆运动速度）

伪逆矩阵是一种适用于一般长方形矩阵的广义逆矩阵定义，方阵的伪逆矩阵与逆矩阵相同。
$$A^+=(A^TA)^{-1}A^T$$
伪逆运算出现在最小二乘法以及机器人学逆向运动学求关节速度的运算中。工程学经常利用伪逆运算取代求逆运算，将只适用于方阵的算法推广到全部矩阵

---
## 转置 Transpose

+ **适用于** - 所有矩阵
+ **符号** - $A^T$
+ **相关概念** - 共轭转置

矩阵$A$的转置矩阵即所有元素关于对角线镜像对称的矩阵
$$A^T=\begin{bmatrix}a&b\\c&d\\e&f\end{bmatrix}^T=\begin{bmatrix}a&c&e\\b&d&f\end{bmatrix}$$
### 转置运算的性质

+ 转置会调转乘法运算顺序
$$(ABC)^{T}=C^{T}B^{T}A^{T}$$
+ 求逆与转置运算顺序可换
$$(A^{-1})^T=(A^T)^{-1}$$

---
## 共轭转置 Conjugate Transpose

+ **适用于** - 所有矩阵
+ **符号** - $A^*$

对于复数矩阵，共轭转置是所有元素转置再求共轭；实数矩阵的共轭转置与一般转置相同
$$A^*=\begin{bmatrix}1+i&5-8i\\2-3i&1+i\end{bmatrix}^*=\begin{bmatrix}1-i&2+3i\\5+8i&1-i\end{bmatrix}$$

---
## 特征值与特征向量 Eigenvalue & Eigenvector

+ **适用于** - 方阵
+ **符号** - $\lambda_i$（特征值）
+ **相关概念** - 特征向量、特征值、特征多项式、特征方程、代数重数、几何重数
+ **相关运算** - [[#相似对角化 Diagonalization|相似对角化]]、[[#若尔当标准型 Jordan Normal Form|若尔当标准型]]

特征值（倍乘系数）与特征向量（映射不变向）是方阵的重要性质，也是相似对角化或若尔当标准化的前提

### 定义 Definition

观察下面的式子，式中的向量$v$经过矩阵$A$的映射变换后，结果仍然与原向量的方向相同，只是大小变为原来的$\lambda$倍。
$$Av=\lambda v$$
满足上述关系的**非零**向量$v$就是矩阵$A$的一个**特征向量（Eigenvector）**，对应的伸缩因子$\lambda$即为矩阵$A$的一个**特征值（Eigenvalue）**，特征值和特征向量总是一一对应。

将上式所有项移到等式一侧得到以下式子
$$(\lambda I-A)v=0$$
由于特征向量$v$是非零向量，因此前面的矩阵必为零
$$\det(\lambda I-A)=0$$
这个等式就是矩阵$A$的**特征方程（Characteristic Formula）**，等号左半部分称为**特征多项式（Characteristic Polynomial）**，求解特征方程即可得到特征值

利用特征向量组成的矩阵可以对原矩阵$A$进行[[#相似对角化 Diagonalization|相似对角化]]或求其[[#若尔当标准型 Jordan Normal Form|若尔当标准型]]

### 特征值、相似对角阵、若尔当型的求解

1. **求特征值**：求解特征方程$\det(\lambda I-A)=0$，特征方程根的数量（包括重根）总是等于矩阵阶数

2. **求特征值$\lambda_i$的特征向量$v_i$**：求解$(\lambda_i I-A)v_i=0$，这是一个$n$元一次方程

3. **If - 可相似对角化？**：若矩阵的所有特征值$\lambda_1,\cdots,\lambda_n$都无重根，则证明矩阵$A$是[[🗃 矩阵分类 Matrix Classification#可对角化矩阵 Diagonalizable Matrix|可相似对角化矩阵]]，否则只能变换为Jordan标准型
	+ <span style="color: green">YES</span>
		+ **求相似对角化变换矩阵$Q$**：将$n$个特征向量按求解顺序排列成$n\times n$的矩阵即得到相似变换矩阵$Q$
	+ <span style="color: red">NO</span>
		+ **求特征值$\lambda_i$的广义特征向量**$v_{i1},v_{i2},...v_{i(n-1)}$：若特征值$\lambda_i$有$q$个重根，则有$q-1$个广义特征向量；把上式右侧的0换成求得的特征向量，可解得第一个广义特征向量；再将第一个广义特征向量放到等式右侧，解得第二个…以此类推，即可求得$q-1$个广义特征向量。（本质上是求解$(\lambda_i I-A)^mv=0$）
		
		+ **求Jordan相似变换矩阵$Q$**：将以上求得若干个特征值的特征向量、广义特征向量写成列向量，按求解顺序排列成$n\times n$的矩阵，这就是Jordan相似变换矩阵$Q$。
	
4. **求相似对角阵或Jordan标准型**：$\bar{A}=Q^{-1}AQ$

### 小总结

+ **定义式**：$Av=\lambda v$
+ **特征多项式**：$\det(\lambda I-A)$
+ **特征方程**：$\det(\lambda I-A)=0$

+ **特征值**$\lambda$：特征向量映射变换的伸缩因子，特征方程的根，数量等于矩阵阶数$n$
	+ **代数重数**：特征值$\lambda_i$的重根个数，也是它在Jordan标准型对角线上的出现次数
	+ **几何重数**：特征值$\lambda_i$在Jordan标准型上所占有的Jordan小分块个数
+ **特征向量**$v$：与矩阵$A$相乘不变向的向量，每个相异特征值只有一个特征向量
	+ **广义特征向量**：满足$(\lambda_i I-A)^mv=0$且$(\lambda_i I-A)v\neq0$，有$n$重根的特征值有$n-1$个广义特征向量

---
## 秩 Rank

+ **适用于** - 所有矩阵
+ **符号** - $\mathrm{rank}(A)$
+ **相关概念** - 行阶梯矩阵

矩阵的秩分为行秩（Row Rank）与列秩（Column Rank），行秩指的是线性无关的**行向量**个数，列秩指的是线性线性无关的**列向量**个数。矩阵的行秩和列秩总是相等，因此又统称为**秩**（Rank）
$$rank(A)=rank(\begin{bmatrix}1&2&2&3\\1&3&3&1\\2&4&4&6\end{bmatrix})=2$$
矩阵的秩的最大可能取值总是等于矩阵行数$m$、列数$n$之中**较小**的值，若矩阵的秩等于其最大可能值，则称为**满秩（Full Rank）**
$$rank(B)=rank(\begin{bmatrix}1&2&3\\4&5&6\end{bmatrix})=2=\min(m,n)$$
### 秩的求解

#### 高斯消元法 Gaussian Elimination Method

使用行初等变换将矩阵$A$变为行阶梯形式（Row Echelon Form），由于行阶梯形式矩阵的所有非零行之间都是线性无关的，其非零行的数量即为原矩阵$A$的秩

#### 子阵行列式法 Submatrix Determinant Method

矩阵$A$的秩等价于其行列式不为0的最大子方阵的阶数


---
## 行空间与列空间 Row and Column Space

+ **适用于** - 所有矩阵

矩阵的行空间与列空间分别指的是


---
## 零空间 Nullspace / 核 Kernel

+ **适用于** - 所有矩阵
+ **符号** - $\mathrm{Null}(A)$ 或 $\mathrm{ker}(A)$

矩阵$A$的零空间或核指的是齐次线性方程组$Ax=0$的解空间，求解方法是使用[高斯消元法](#高斯消元法%20Gaussian%20Elimination%20Method)
$$\mathrm{Null}(A)=\mathrm{ker}(A)=\{x\in V|Ax=0\}$$




---
## 迹 Trace

+ **适用于** - 方阵
+ **符号** - $\mathrm{tr}(A)$ 

矩阵$A$的迹是其对角线上所有元素之和，也是其所有特征值之和
$$tr(A)=tr(\begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix})=\sum_{i=0}^n a_{ii}=\sum_{i=0}^n \lambda_i$$

---
## 加减 Addition & Subtraction

+ **适用于** - 两个大小完全相同的矩阵
+ **符号** - $A\pm B$

两个矩阵的加减法是简单的逐元素加减

$$A+B=\begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix}+\begin{bmatrix}2&4&6\\1&5&9\\3&7&8\end{bmatrix}=\begin{bmatrix}3&6&9\\5&10&15\\10&15&17\end{bmatrix}$$
$$A-B=\begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix}-\begin{bmatrix}2&4&6\\1&5&9\\3&7&8\end{bmatrix}=\begin{bmatrix}-1&-2&-3\\3&0&-3\\4&1&1\end{bmatrix}$$

矩阵加减法的性质与标量加减法完全相同，满足交换律、结合律、分配律

$$A+B=B+A$$
$$(A+B)+C=A+(B+C)$$
$$A-B-C=A-(B+C)$$
$$(A+B)C=AC+BC$$

---
## 倍乘 Scalar Multiplication

+ **适用于** - 所有矩阵
+ **符号** - $k A$

矩阵乘一个标量是逐元素相乘
$$k A=3\times \begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix}=\begin{bmatrix}3&6&9\\12&15&18\\21&24&27\end{bmatrix}$$
倍乘运算可以用矩阵乘法表示
$$kA=kIA=A(kI)=3\times\begin{bmatrix}1 &0&0\\0&1&0\\0&0&1 \end{bmatrix}\begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix}=\begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix}\times3\times\begin{bmatrix}1 &0&0\\0&1&0\\0&0&1 \end{bmatrix}$$

---
## 逐项乘 Hadamard Multiplication

+ **适用于** - 所有矩阵
+ **符号** -  $A\odot B$
+ **相关领域** - 机器学习、数据科学

矩阵的逐项乘法又称为阿达玛乘积，两个矩阵逐项乘的运算要求矩阵规模相同，逐项乘常用在计算机编程领域，如表示

$$A\odot B=\begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix}\begin{bmatrix}1&0&1\\0&1&0\\1&0&1\end{bmatrix}=\begin{bmatrix}1&0&3\\0&5&0\\7&0&9\end{bmatrix}$$




---
## 乘法 Multiplication

+ **适用于** - 左侧矩阵的列数与右侧矩阵的行数相等
+ **符号** -  $AB$

矩阵的乘法是最重要的矩阵运算之一，其性质和运算规律和标量乘法有很大区别

### 四种角度


### 可换矩阵 Commuting Matrix


---
## 乘方 Power

+ **适用于** - 方阵
+ **符号** -  $A^k$

方阵$A$的乘方定义为$k$个方阵乘在一起的结果，是标量乘方的推广；非方阵的普通矩阵没有乘方

$$A^k=\prod_{i=1}^k A=\begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix}\begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix}\cdots\begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix}$$
### 乘方的性质

+ 方阵的零次幂是单位矩阵$I$
$$A^0=I$$
+ 方阵的一次幂是其本身
$$A^1=A$$

---
## 初等变换 Elementary Operation

+ **适用于** - 所有矩阵

初等变换是对矩阵的整行或整列进行的互换、倍乘、叠加三种操作的统称，对行的操作称为行变换，对列的操作称为列变换。

初等变换可以用矩阵乘法表示，表示一步初等变换的矩阵称为[[🗃 矩阵分类 Matrix Classification#初等矩阵 Elementary Matrix|初等矩阵]]

1. **互换**：矩阵的两行或两列交换位置
$$CA=\begin{bmatrix}0&1\\1&0\end{bmatrix}\begin{bmatrix}\color{green}1&\color{green}2&\color{green}3\\\color{orange}4&\color{orange}5&\color{orange}6\end{bmatrix}=\begin{bmatrix}\color{orange}4&\color{orange}5&\color{orange}6\\\color{green}1&\color{green}2&\color{green}3\end{bmatrix}$$
$$AB=\begin{bmatrix}1&\color{green}2&\color{orange}3\\4&\color{green}5&\color{orange}6\end{bmatrix}\begin{bmatrix}1&0&0\\0&0&1\\0&1&0\end{bmatrix}=\begin{bmatrix}1&\color{orange}3&\color{green}2\\4&\color{orange}6&\color{green}5\end{bmatrix}$$
2. **倍乘**：矩阵的整行或整列乘$k$倍（不可乘0）
$$CA=\begin{bmatrix}2&0\\0&1\end{bmatrix}\begin{bmatrix}\color{orange}1&\color{orange}2&\color{orange}3\\4&5&6\end{bmatrix}=\begin{bmatrix}\color{orange}2&\color{orange}4&\color{orange}6\\4&5&6\end{bmatrix}$$
$$AB=\begin{bmatrix}\color{orange}1&2&3\\\color{orange}4&5&6\end{bmatrix}\begin{bmatrix}2&0&0\\0&1&0\\0&0&1\end{bmatrix}=\begin{bmatrix}\color{orange}2&2&3\\\color{orange}8&5&6\end{bmatrix}$$
3. **叠加**：矩阵的整行或整列的$k$倍，加到另一行或列上
$$CA=\begin{bmatrix}1&0\\2&1\end{bmatrix}\begin{bmatrix}\color{orange}1&\color{orange}2&\color{orange}3\\\color{red}4&\color{red}5&\color{red}6\end{bmatrix}=\begin{bmatrix}1&2&3\\\color{red}6&\color{red}9&\color{red}12\end{bmatrix}$$
$$AB=\begin{bmatrix}\color{orange}1&\color{red}2&3\\\color{orange}4&\color{red}5&6\end{bmatrix}\begin{bmatrix}1&2&0\\0&1&0\\0&0&1\end{bmatrix}=\begin{bmatrix}\color{orange}1&\color{red}4&3\\\color{orange}4&\color{red}13&6\end{bmatrix}$$

---
## 高斯消元法 Gaussian Elimination

高斯消元法利用初等行变换将矩阵化为行阶梯矩阵的形式，常用于

+ 求解一次方程组（初等行变换与方程组的相消是等价操作）
+ 求解矩阵的秩
+ 求解矩阵的零空间



---
## 相似变换 Similarity Transformation

+ **适用于** - 方阵
+ **相关概念** - 相似矩阵、相似对角化、若尔当标准型

矩阵$A,B$同阶，如果存在一可逆矩阵$P$，使得$A,B$满足下列关系，则$A,B$互为**相似矩阵**，也称$A,B$之间是相似的（Similar）
$$P^{-1}AP=B$$
矩阵的相似对角化、求若尔当标准型都属于相似变换的一种


---
## 相似对角化 Diagonalization

+ **适用于** - [[🗃 矩阵分类 Matrix Classification#可对角化矩阵 Diagonalizable Matrix|可相似对角化矩阵]]
+ **相关概念** - 相似变换、若尔当标准型

相似对角化是通过相似变换将一个方阵变为一个对角矩阵的运算过程，其一般形式是若尔当标准化。并不是所有方阵都能够化为对角矩阵，不能对角化的方阵只能化为若尔当标准型。


### 求相似对角矩阵

参见[[#特征值、相似对角阵、若尔当型的求解]]


---
## 若尔当标准型 Jordan Normal Form

+ **适用于** - 所有矩阵
+ **相关概念** - 相似变换、相似对角化

矩阵$A$化为Jordan标准型是相似对角化操作的广义形式，因此也是一种相似矩阵，所有矩阵都能化为若尔当标准型，[[🗃 矩阵分类 Matrix Classification#可对角化矩阵 Diagonalizable Matrix|可相似对角化矩阵]]的若尔当标准型即为其相似对角矩阵。

Jordan标准型$\bar{A}$对角线上的值对应矩阵$A$的特征值$\lambda_1,\lambda_2,...,\lambda_n$，对角线元素上方一格的值可能为0或1，其余位置的值均为0

+ **Jordan小分块**：指的是对角线上方一格的值严格为1的Jordan矩阵，普通的Jordan阵在对角线上总是可以分为几个小Jordan分块。
$$\bar{A}_1=\begin{bmatrix}\color{brown}1&1\\&\color{brown}1\end{bmatrix}\quad \bar{A}_{21}=\begin{bmatrix}\color{brown}\color{orange}2\end{bmatrix}\quad \bar{A}_{22}=\begin{bmatrix}\color{orange}2&1\\&\color{orange}2\end{bmatrix}\quad \bar{A}_{3}=\begin{bmatrix}\color{green}5\end{bmatrix}$$
+ **代数重数（Algebraic Multiplicity）**：某个特征值$\lambda_i$的重根数量，即它在Jordan矩阵对角线出现的次数
+ **几何重数（Geometric Multiplicity）**：某个特征值$\lambda_i$占有的小Jordan分块数量

从以下Jordan标准型可以看出原矩阵$A$有三个特征值（$\lambda_1=1,\lambda_2=2,\lambda_3=5$），且$\lambda_1$有2个重根，$\lambda_2$有3个重根；$\lambda_2$还占有两个Jordan小分块，因此其几何重数为2

$$\bar{A}=\begin{bmatrix}\color{brown}1&1&&&&\\&\color{brown}1&&&\\&&\color{orange}2&&&\\&&&\color{orange}2&1&\\&&&&\color{orange}2\\&&&&&\color{green}5\end{bmatrix}$$

### 若尔当标准型求解

参见[[#特征值、相似对角阵、若尔当型的求解]]


---
## 上下三角分解 LU Decomposition

+ **适用于** - 方阵

上下三角分解是将一个方阵$A$分解为一个下三角矩阵$L$和一个上三角矩阵$U$的过程
$$A=LU$$


---
## 正交上三角分解 QR Decomposition



---
## 奇异值分解 Singular Value Decomposition

+ **适用于** - 所有复矩阵
+ **符号** - $A=U\Sigma V^*$

奇异值分解可以将任意一个复矩阵拆分成三个相乘的矩阵
$$A=U\Sigma V^*$$


### 奇异值 Singular Value



### 条件数 Condition Number




---
## 矩阵指数 Matrix Exponential

+ **适用于** - 方阵
+ **符号** - $e^A$


---
## 导数 Derivative


---
## 积分 Integral








---
## 矩阵运算的编程实现 Matrix Operations by Coding

大部分支持矩阵运算的软件或库都提供优化好的矩阵运算函数





---
## 矩阵与向量 Matrix & Vector 

矩阵和向量的联系十分紧密，部分向量的运算可以推广到矩阵，部分矩阵的运算也可以适用于向量

+ 两者同属张量：矩阵是二维张量，向量是一维张量
+ 向量是一种矩阵：列向量可以看作列数为1的矩阵，行向量可以看作行数为1的矩阵

### 向量伸缩的矩阵形式 Vector Scaling in Matrix

向量的长度伸缩在矩阵形式下要多乘一个单位矩阵
$$\lambda v=\lambda Iv$$

### 叉积矩阵 Cross Product Matrix

向量的叉积运算可以用反对称矩阵（Skew-symmetric Matrix）与向量的乘法表示
$$A\times B=[A]_\times B=\begin{bmatrix}0 &-a_3& a_2\\a_3&0&-a_1\\-a_2&a_1&0\end{bmatrix} \begin{bmatrix}b_1 \\ b_2 \\ b_3\end{bmatrix}$$






---
## 雅可比矩阵 Jacobian Matrix

