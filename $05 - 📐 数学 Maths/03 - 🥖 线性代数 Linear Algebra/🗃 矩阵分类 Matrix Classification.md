+ **矩阵运算**：[[⚙️ 矩阵运算 Matrix Operations]]






+ 特殊矩阵 Special Matrix
	+ 矩阵特性 By characteristics
		+ [[#零矩阵 Zero Matrix]]
		+ [[#阶梯矩阵 Echelon Matrix]]
		+ [[#方阵 Square Matrix]]
		+ [[#单位矩阵 Identity Matrix]]
		+ [[#初等矩阵 Elementary Matrix]]
		+ [[#可逆与奇异矩阵 Invertible & Singular Matrix]]
		+ [[#三角矩阵 Triangular Matrix]]
		+ [[#对角矩阵 Diagonal Matrix]]
		+ [[#可对角化矩阵 Diagonalizable Matrix]]
		+ [[#对称矩阵 Symmetric Matrix]]
		+ [[#定矩阵 Definite Matrix]]
		+ [[#正交矩阵 Orthogonal Matrix]]
		+ [[#幂零矩阵 Nullpotent Matrix]]
	+ 矩阵关系 By relationship
		+ [[#分块矩阵 Block matrix]]
		+ [[#相似矩阵 Similar Matrices]]
		+ [[#合同矩阵 Congruence Matrices]]

---
## 零矩阵 Zero Matrix

零矩阵指的是所有元素均为0的矩阵
$$\begin{bmatrix}0 &0&0\\0&0&0\end{bmatrix}\quad\begin{bmatrix}0 &0\\0&0\end{bmatrix}$$
零矩阵的性质类似标量0，两个相同矩阵的差即为相同大小的零矩阵
$$A-A=0$$


---
## 阶梯矩阵 Echelon Matrix

+ **相关概念** - 高斯消元法

阶梯矩阵可以指行阶梯矩阵和列阶梯矩阵，比较常见的是**行阶梯矩阵**，它是高斯消元法的最终结果（参见[[#高斯消元法 Gaussian Elimination]]），任何矩阵都可以通过**行初等变换**化为行阶梯矩阵形式

行阶梯矩阵的特点是每一行的零元素位于左侧，且越靠下的行前面的零元素序列越长，全零行位于最下方。矩阵左下方含零的部分从左往右看酷似向下走的台阶，因此称为阶梯矩阵。

阶梯矩阵每一行从左到右第一个非零元素被称为**首项系数（Pivot）**

$$\begin{bmatrix}\color{green}1&2&3&4&3\\\color{orange}0&\color{green}3&2&0&2\\\color{orange}0&\color{orange}0&\color{orange}0&\color{green}3&7\\\color{orange}0&\color{orange}0&\color{orange}0&\color{orange}0&\color{orange}0\end{bmatrix}$$

一种更严格的行阶梯矩阵称为简化行阶梯矩阵（Reduced Row Echelon Form）或行规范形式（Row Canonical Form），它要求每一行的首项系数必须为1，且首项系数所在列的其他元素皆为0

$$\begin{bmatrix}\color{green}1&\color{gray}0&3&\color{gray}0&3\\\color{orange}0&\color{green}1&2&\color{gray}0&2\\\color{orange}0&\color{orange}0&\color{orange}0&\color{green}1&7\\\color{orange}0&\color{orange}0&\color{orange}0&\color{orange}0&\color{orange}0\end{bmatrix}$$

列阶梯矩阵的定义和行阶梯矩阵刚好是转置关系，不过很少使用。


---
## 方阵 Square Matrix

方阵是一类重要的矩阵，在工程领域出现的频率远高于普通的长方形矩阵。
$$\begin{bmatrix}a&b\\c&d\end{bmatrix}\quad\begin{bmatrix}a&b&c\\d&e&f\\g&h&i\end{bmatrix}\quad\begin{bmatrix}a&b&c&d\\e&f&g&h\\i&j&k&l\\m&n&o&p\end{bmatrix}$$
许多矩阵运算与性质，如求逆、特征向量只适用于方阵。大部分有特殊性质和用途的矩阵都属于方阵，如三角矩阵、单位矩阵、正交矩阵


---
## 单位矩阵 Identity Matrix

+ **超集** - 方阵、对角矩阵、对称矩阵
+ **符号** - $I$或$E$

单位矩阵是对角线元素全为1的特殊对称矩阵
$$I_2=\begin{bmatrix}1&0\\0&1\end{bmatrix}\quad I_3=\begin{bmatrix}1&0&0\\0&1&0\\0&0&1\end{bmatrix}\quad I_4=\begin{bmatrix}1&0&0&0\\0&1&0&0\\0&0&1&0\\0&0&0&1\end{bmatrix}$$
单位矩阵$I$乘任何矩阵$A$（假设可以乘）都等于矩阵$A$自身，类似标量1的性质
$$AI=A$$

---
## 初等矩阵 Elementary Matrix

+ **超集** - 方阵
+ **相关运算** - [[⚙️ 矩阵运算 Matrix Operations#初等变换 Elementary Operation|初等变换]]


初等矩阵是单位矩阵进行**一步初等变换**得到的矩阵，初等矩阵乘在矩阵$A$左侧表示对$A$进行行变换，乘在右侧则是列变换。


---
## 可逆与奇异矩阵 Invertible & Singular Matrix

+ **超集** - 方阵

可逆矩阵指的是行列式不为零，具有逆矩阵的矩阵，奇异矩阵则刚好相反，指的是不可逆矩阵。


---
## 三角矩阵 Triangular Matrix



---
## 对角矩阵 Diagonal Matrix




---
## 可对角化矩阵 Diagonalizable Matrix


---
## 对称矩阵 Symmetric Matrix



---
## 定矩阵 Definite Matrix 



---
## 正交矩阵 Orthogonal Matrix


---
## 幂零矩阵 Nullpotent Matrix

 + 

---
## 分块矩阵 Block Matrix


---
## 相似矩阵 Similar Matrices

+ 


---
## 合同矩阵 Congruence Matrices


