
+ [[#矩阵含义 Matrix Representation]]

+ 一元运算及性质 Unary Operations & Properties
	+ [[#行列式 Determinant]]
		+ [[#高阶行列式求解 Large Determinant Solution]]
			+ [[#拉普拉斯展开法 Laplace Expansion]]
	+ [[#求逆 Inverse]]
		+ [[#求解 Solution]]
			+ [[#伴随矩阵法 Adjugate Matrix Method]]
			+ [[#初等变换法 Elementary Transform Method]]
		+ [[#性质 Property]]
		+ [[#伪逆 Pseudo-inverse]]
	+ [[#转置 Transpose]]
		+ [[#共轭转置 Conjugate Transpose]]
	+ [[#相似变换 Similar Transform]]
	+ [[#特征值与特征向量 Eigenvalue & Eigenvector]]
		+ [[#定义 Definition]]
		+ [[#若尔当标准型 Jordan Normal Form]]
		+ [[#求解 Solution]]
		+ [[#小总结 Conclusion]]
	+ [[#秩 Rank]]
		+ [[#求解 Solution]]
			+ [[#高斯消元法 Gaussian Elimination Method]]
			+ [[#子阵行列式法 Submatrix Determinant Method]]
	+ [[#迹 Trace]]
	+ [[#矩阵指数 Matrix Exponential]]

+ 二元运算 Binary Operations
	+ [[#加减 Addition & Subtraction]]
	+ [[#标量乘 Scalar Multiplication]]
	+ [[#乘法 Multiplication]]
		+ [[#
	+ [[#初等变换 Elementary Operation]]
	+ [[#高斯消元法 Gaussian Elimination]]

+ 特殊矩阵 Special Matrix
	+ 矩阵特性 By characteristics
		+ [[#零矩阵 Zero Matrix]]
		+ [[#阶梯矩阵 Echelon Matrix]]
		+ [[#方阵 Square Matrix]]
		+ [[#单位矩阵 Identity Matrix]]
		+ [[#初等矩阵 Elementary Matrix]]
		+ [[#可逆矩阵与奇异矩阵 Invertible Matrix & Singular Matrix]]
		+ [[#三角矩阵 Triangular Matrix]]
		+ [[#对角矩阵 Diagonal Matrix]]
		+ [[#可对角化矩阵 Diagonalizable Matrix]]
		+ [[#对称矩阵 Symmetric Matrix]]
		+ [[#定矩阵 Definite Matrix]]
		+ [[#可逆矩阵与奇异矩阵 Invertible Matrix & Singular Matrix]]
		+ [[#正交矩阵 Orthogonal Matrix]]
		+ [[#幂零矩阵 Nullpotent Matrix]]
	+ 矩阵关系 By relationship
		+ [[#分块矩阵 Block matrix]]
		+ [[#相似矩阵 Similar Matrices]]
		+ [[#合同矩阵 Congruence Matrices]]

+ 其他话题 Other Topics
	+ [[#矩阵运算的编程实现 Matrix Operations by Coding]]
	+ [[#矩阵与向量 Matrix & Vector]]
	+ [[#雅可比矩阵 Jacobian Matrix]]


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
+ **代数余子式**$A_{ij}$：元素$a_{ij}$的代数余子式是原行列式删去$a_{ij}$所在的行和列剩下的行列式，乘以一个决定正负的因子$(-1)^{i+j}$

$$a_{01}\begin{cases}i=1\\j=2\end{cases} \quad\to\quad A=\begin{bmatrix}\color{orange}a&\color{red}b&\color{orange}c\\\color{green}d&\color{orange}e&\color{green}f\\\color{green}g&\color{orange}h&\color{green}i\end{bmatrix} \quad\to \quad A_{01}=\begin{bmatrix}\color{green}d&\color{green}f\\\color{green}g&\color{green}i\end{bmatrix}\times(-1)^{1+2}=-\begin{bmatrix}d&f\\g&i\end{bmatrix}$$

比如说，选择第二列
$$\det(A)=\det(\begin{bmatrix}a&\color{red}b&c\\d&\color{red}e&f\\g&\color{red}h&i\end{bmatrix})=-b\begin{bmatrix}d&f\\g&i\end{bmatrix}+e\begin{bmatrix}a&c\\g&i\end{bmatrix}-h\begin{bmatrix}a&c\\d&f\end{bmatrix}$$

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

### 求解 Solution

#### 伴随矩阵法 Adjugate Matrix Method

矩阵$A$的逆等于其伴随矩阵除以行列式
$$A^{-1}=\frac{adj(A)}{|A|}$$
+ **伴随矩阵**$adj(A)$：由矩阵$A$所有元素的代数余子式组成的矩阵的转置
$$A=\begin{bmatrix}a_{11}&a_{12}\\a_{21}&a_{22}\end{bmatrix}\quad\to\quad adj(A)=\begin{bmatrix}A_{11}&A_{12}\\A_{21}&A_{22}\end{bmatrix}^T=\begin{bmatrix}A_{11}&A_{21}\\A_{12}&A_{22}\end{bmatrix}$$

#### 初等变换法 Elementary Transform Method

将一个同阶的单位矩阵$I$并在矩阵$A$的右侧，组成一个$n\times2n$的长方形矩阵，对这个矩阵进行**行变换**
，当左侧原本的矩阵$A$变成单位矩阵$I$时，右侧原本的单位矩阵$I$就变成$A$的逆矩阵
$$\begin{bmatrix}A&I\end{bmatrix}\to\begin{bmatrix}I&A^{-1}\end{bmatrix}$$
其原理如下（矩阵$B$表示进行的所有行变换）
$$AB=I\to B=A^{-1}$$
$$IB=IA^{-1}=A^{-1}$$

### 性质 Property

+ 矩阵与自身的逆相乘得到单位矩阵
$$AA^{-1}=A^{-1}A=I$$
+ 求逆会调转乘法运算顺序
$$(ABC)^{-1}=C^{-1}B^{-1}A^{-1}$$
+ 求逆与转置运算顺序可换
$$(A^{-1})^T=(A^T)^{-1}$$

### 伪逆 Pseudo-inverse

+ **适用于** - 所有矩阵
+ **符号** - $A^+$
+ **相关领域** - 机器人学（雅可比矩阵）

伪逆矩阵是一种适用于一般长方形矩阵的广义逆矩阵定义，方阵的伪逆矩阵仍是一般的逆矩阵
$$A^+=(A^TA)^{-1}A^T$$

---
## 转置 Transpose

+ **适用于** - 所有矩阵
+ **符号** - $A^T$

矩阵$A$的转置矩阵即所有元素关于对角线镜像对称的矩阵
$$A^T=\begin{bmatrix}a&b\\c&d\\e&f\end{bmatrix}^T=\begin{bmatrix}a&c&e\\b&d&f\end{bmatrix}$$

### 共轭转置 Conjugate Transpose

+ **适用于** - 所有矩阵
+ **符号** - $A^*$

对于复数矩阵，共轭转置是所有元素转置再求共轭；实数矩阵的共轭转置与一般转置相同
$$A^*=\begin{bmatrix}1+i&5-8i\\2-3i&1+i\end{bmatrix}^*=\begin{bmatrix}1-i&2+3i\\5+8i&1-i\end{bmatrix}$$

---
## 相似变换 Similar Transform

+ **适用于** - 方阵
+ **相关概念** - 相似矩阵、相似对角化、若尔当标准型

矩阵$A,B$同阶，如果存在一可逆矩阵$P$，使得$A,B$满足下列关系，则$A,B$互为**相似矩阵**
$$P^{-1}AP=B$$
矩阵的相似对角化、求若尔当标准型都属于相似变换

---
## 特征值与特征向量 Eigenvalue & Eigenvector

+ **适用于** - 方阵
+ **符号** - $\lambda_i$（特征值）
+ **相关概念** - 特征向量、特征值、特征多项式、特征方程、代数重数、几何重数、若尔当标准型

特征值与特征向量是方阵的重要性质。

### 定义 Definition

观察下面的式子，式中的向量$v$经过矩阵$A$的映射变换后，结果仍然与原向量的方向相同，只是大小变为原来的$\lambda$倍。
$$Av=\lambda v$$
满足上述关系的**非零**向量$v$就是矩阵$A$的一个**特征向量（Eigenvector）**，对应的伸缩因子$\lambda$即为矩阵$A$的一个**特征值（Eigenvalue）**，特征值和特征向量总是一一对应。

将上式所有项移到等式一侧得到以下式子
$$(\lambda I-A)v=0$$
由于特征向量$v$是非零向量，因此前面的矩阵必为零
$$\det(\lambda I-A)=0$$
这个等式就是矩阵$A$的**特征方程（Characteristic Formula）**，等号左半部分称为**特征多项式（Characteristic Polynomial）**，求解特征方程即可得到特征值

与特征值密切相关的概念是矩阵的若尔当标准型。


### 若尔当标准型 Jordan Normal Form

矩阵$A$的Jordan标准型$\bar{A}$是一种特殊的相似矩阵，其对角线上的值对应矩阵$A$的特征值$\lambda_1,\lambda_2,...,\lambda_n$，对角线元素上方一格的值可能为0或1，其余位置的值均为0

+ **Jordan小分块**：指的是对角线上方一格的值严格为1的Jordan矩阵，普通的Jordan阵在对角线上总是可以分为几个小Jordan分块。
+ **代数重数（Algebraic Multiplicity）**：某个特征值$\lambda_i$的重根数量，即它在Jordan矩阵对角线出现的次数
+ **几何重数（Geometric Multiplicity）**：某个特征值$\lambda_i$占有的小Jordan分块数量

从以下Jordan标准型可以看出原矩阵$A$有三个特征值（$\lambda_1=1,\lambda_2=2,\lambda_3=5$），且$\lambda_1$有2个重根，$\lambda_2$有3个重根；$\lambda_2$还占有两个Jordan小分块，因此其几何重数为2

$$\bar{A}=\begin{bmatrix}\color{brown}1&1&&&&\\&\color{brown}1&&&\\&&\color{orange}2&&&\\&&&\color{orange}2&1&\\&&&&\color{orange}2\\&&&&&\color{green}5\end{bmatrix}$$

### 求解 Solution

1. **求特征值**：求解特征方程$\det(\lambda I-A)=0$，特征方程根的数量（包括重根）总是等于矩阵阶数

2. **求特征值$\lambda_i$的特征向量$v_i$**：求解$(\lambda_i I-A)v_i=0$，这是一个$n$元一次方程

3. **求特征值$\lambda_i$的广义特征向量**$v_{i1},v_{i2},...v_{i(n-1)}$：若特征值$\lambda_i$有$n$个重根，则有$n-1$个广义特征向量；把上式右侧的0换成求得的特征向量，可解得第一个广义特征向量；再将第一个广义特征向量放到等式右侧，解得第二个…以此类推，即可求得$n-1$个广义特征向量。（本质上是求解$(\lambda_i I-A)^mv=0$）

4. **求Jordan相似变换矩阵$Q$**：将以上求得若干个特征值的特征向量、广义特征向量写成列向量，按求解顺序排列好，则组成一个$n\times n$的矩阵，这就是Jordan相似变换矩阵$Q$。

5. **求Jordan标准型**：$\bar{A}=Q^{-1}AQ$


### 小总结 Conclusion 

+ **定义式**：$Av=\lambda v$
+ **特征多项式**：$\det(\lambda I-A)$
+ **特征方程**：$\det(\lambda I-A)=0$

+ **特征值**$\lambda$：特征向量映射变换的伸缩因子，特征方程的根，数量等于矩阵阶数$n$
	+ **代数重数**：特征值$\lambda_i$的重根个数，也是它在Jordan标准型对角线上的出现次数
	+ **几何重数**：特征值$\lambda_i$在Jordan标准型上所占有的Jordan小分块个数
+ **特征向量**$v$：与矩阵$A$相乘不变向的向量，每个相异特征值只有一个特征向量
	+ **广义特征向量**：满足$(\lambda_i I-A)^mv=0$，有$n$重根的特征值有$n-1$个广义特征向量

---
## 秩 Rank

+ **适用于** - 所有矩阵
+ **符号** - $rank(A)$
+ **相关概念** - 行阶梯矩阵

矩阵的秩分为行秩（Row Rank）与列秩（Column Rank），行秩指的是线性无关的**行向量**个数，列秩指的是线性线性无关的**列向量**个数。所有矩阵的行秩和列秩都相等，因此又统称为秩（Rank）
$$rank(A)=rank(\begin{bmatrix}1&2&2&3\\1&3&3&1\\2&4&4&6\end{bmatrix})=2$$
矩阵的秩的最大可能取值总是等于矩阵行数$m$、列数$n$之中**较小**的值，若矩阵的秩等于其最大可能值，则称为**满秩（Full Rank）**
$$rank(B)=rank(\begin{bmatrix}1&2&3\\4&5&6\end{bmatrix})=2=\min(m,n)$$
### 求解 Solution

#### 高斯消元法 Gaussian Elimination Method

使用行初等变换将矩阵$A$变为行阶梯形式（Row Echelon Form），由于行阶梯形式矩阵的所有非零行之间都是线性无关的，其非零行的数量即为原矩阵$A$的秩

#### 子阵行列式法 Submatrix Determinant Method

矩阵$A$的秩等价于其行列式不为0的最大子方阵的阶数

---
## 迹 Trace

+ **适用于** - 方阵
+ **符号** - $tr(A)$ 

矩阵$A$的迹是其对角线上所有元素之和，也是其所有特征值之和
$$tr(A)=tr(\begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix})=\sum_{i=0}^n a_{ii}=\sum_{i=0}^n \lambda_i$$

---
## 矩阵指数 Matrix Exponential

+ **适用于** - 方阵
+ **符号** - $e^A$


---
## 加减 Addition & Subtraction

+ **适用于** - 两个大小完全相同的矩阵
+ **符号** - $A+B$

矩阵的加减法是简单的逐元素加减

$$A+B=\begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix}+\begin{bmatrix}2&4&6\\1&5&9\\3&7&8\end{bmatrix}=\begin{bmatrix}3&6&9\\5&10&15\\10&15&17\end{bmatrix}$$
$$A-B=\begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix}-\begin{bmatrix}2&4&6\\1&5&9\\3&7&8\end{bmatrix}=\begin{bmatrix}-1&-2&-3\\3&0&-3\\4&1&1\end{bmatrix}$$

矩阵加减法的性质与标量加减法完全相同，满足交换律、结合律、分配律

$$A+B=B+A$$
$$(A+B)+C=A+(B+C)$$
$$A-B-C=A-(B+C)$$
$$(A+B)C=AC+BC$$

---
## 标量乘 Scalar Multiplication

+ **适用于** - 所有矩阵
+ **符号** - $\lambda A$

矩阵乘一个标量是逐元素相乘

$$\lambda A=3\times \begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix}=\begin{bmatrix}3&6&9\\12&15&18\\21&24&27\end{bmatrix}$$

---
## 乘法 Multiplication

+ **适用于** - 左侧矩阵的列数与右侧矩阵的行数相等
+ **符号** -  $AB$

矩阵的乘法是最重要的矩阵运算之一，其性质和运算规律和标量乘法完全不同


### 四种角度


### 可换矩阵 Commuting Matrix



### 幂 


---
## 初等变换 Elementary Operation

+ **适用于** - 所有矩阵

初等变换是对矩阵的整行或整列进行的互换、倍乘、叠加三种操作的统称，对行的操作称为行变换，对列的操作称为列变换。

初等变换可以用矩阵乘法表示，表示初等变换的矩阵称为初等矩阵（参见[[#初等矩阵 Elementary Matrix]]）

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



---
## 特殊矩阵 Special Matrix

### 零矩阵 Zero Matrix

零矩阵指的是所有元素均为0的矩阵
$$\begin{bmatrix}0 &0&0\\0&0&0\end{bmatrix}\quad\begin{bmatrix}0 &0\\0&0\end{bmatrix}$$
零矩阵的性质类似标量0，两个相同矩阵的差即为相同大小的零矩阵
$$A-A=0$$

### 阶梯矩阵 Echelon Matrix

+ **相关概念** - 高斯消元法

阶梯矩阵可以指行阶梯矩阵和列阶梯矩阵，比较常见的是行阶梯矩阵，它是高斯消元法的最终结果（参见[[#高斯消元法 Gaussian Elimination]]），任何矩阵都可以通过**行初等变换**化为行阶梯矩阵形式

行阶梯矩阵的特点是每一行的零元素位于左侧，且越靠下的行前面的零元素序列越长，全零行位于最下方。矩阵左下方含零的部分从左往右看酷似向下走的台阶，因此称为阶梯矩阵。

阶梯矩阵每一行从左到右第一个非零元素被称为**首项系数（Pivot）**

$$\begin{bmatrix}\color{green}1&2&3&4&3\\\color{orange}0&\color{green}3&2&0&2\\\color{orange}0&\color{orange}0&\color{orange}0&\color{green}3&7\\\color{orange}0&\color{orange}0&\color{orange}0&\color{orange}0&\color{orange}0\end{bmatrix}$$

一种更严格的行阶梯矩阵称为简化行阶梯矩阵（Reduced Row Echelon Form）或行规范形式（Row Canonical Form），它要求每一行的首项系数必须为1，且首项系数所在列的其他元素皆为0

$$\begin{bmatrix}\color{green}1&\color{gray}0&3&\color{gray}0&3\\\color{orange}0&\color{green}1&2&\color{gray}0&2\\\color{orange}0&\color{orange}0&\color{orange}0&\color{green}1&7\\\color{orange}0&\color{orange}0&\color{orange}0&\color{orange}0&\color{orange}0\end{bmatrix}$$

列阶梯矩阵的定义和行阶梯矩阵刚好是转置关系，不过很少使用。

### 方阵 Square Matrix

方阵是一类重要的矩阵，在工程领域出现的频率远高于普通的长方形矩阵。
$$\begin{bmatrix}a&b\\c&d\end{bmatrix}\quad\begin{bmatrix}a&b&c\\d&e&f\\g&h&i\end{bmatrix}\quad\begin{bmatrix}a&b&c&d\\e&f&g&h\\i&j&k&l\\m&n&o&p\end{bmatrix}$$
许多矩阵运算，如求逆、求特征向量只能用于方阵。大部分有特殊性质和用途的矩阵都属于方阵，如三角矩阵、单位矩阵、正交矩阵

### 单位矩阵 Identity Matrix

+ **必为** - 方阵、对角矩阵、对称矩阵
+ **符号** - $I$或$E$

单位矩阵是对角线元素全为1的特殊对称矩阵
$$I_2=\begin{bmatrix}1&0\\0&1\end{bmatrix}\quad I_3=\begin{bmatrix}1&0&0\\0&1&0\\0&0&1\end{bmatrix}\quad I_4=\begin{bmatrix}1&0&0&0\\0&1&0&0\\0&0&1&0\\0&0&0&1\end{bmatrix}$$
单位矩阵$I$乘任何矩阵$A$（假设可以乘）都等于矩阵$A$自身，类似标量1的性质
$$AI=A$$

### 初等矩阵 Elementary Matrix

+ **必为** - 方阵

初等矩阵是单位矩阵进行**一步初等变换**得到的矩阵，初等矩阵乘在矩阵$A$左侧表示对$A$进行行变换，乘在右侧则是列变换。

（参见[[#初等变换 Elementary Operation]]）

### 可逆矩阵与奇异矩阵 Invertible Matrix & Singular Matrix

+ **必为** - 方阵

可逆矩阵指的是行列式不为零，具有逆矩阵的矩阵，奇异矩阵则刚好相反，指的是不可逆矩阵。


### 三角矩阵 Triangular Matrix




### 对角矩阵 Diagonal Matrix


### 可对角化矩阵 Diagonalizable Matrix


### 对称矩阵 Symmetric Matrix


### 定矩阵 Definite Matrix 


### 正交矩阵 Orthogonal Matrix


### 幂零矩阵 Nullpotent Matrix

 + 

### 分块矩阵 Block Matrix


### 相似矩阵 Similar Matrices

参见[[#相似变换 Similar Transform]]

### 合同矩阵 Congruence Matrices



---
## 矩阵运算的编程实现 Matrix Operations by Coding

大部分支持矩阵运算的软件或库都提供优化好的矩阵运算函数





---
## 矩阵与向量 Matrix & Vector 

矩阵和向量的联系十分紧密，部分向量的运算可以推广到矩阵，部分矩阵的运算也可以适用于向量

+ 两者同属张量：矩阵是二维张量，向量是一维张量
+ 向量是一种矩阵：列向量可以看作列数为1的矩阵，行向量可以看作行数为1的矩阵

### 向量伸缩的矩阵形式

向量的长度伸缩在矩阵形式下要多乘一个单位矩阵
$$\lambda v=\lambda Iv$$

---
## 雅可比矩阵 Jacobian Matrix

