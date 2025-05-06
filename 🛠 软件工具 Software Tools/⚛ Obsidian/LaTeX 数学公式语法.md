理工学科的理论部分需要很多数学知识作基础，因此有输入数学公式的需求。幸运的是，Markdown支持LaTeX格式的数学符号输入，所有数学公式统一用一对美元符号“$”括起来表示，在解释器中渲染为标准的数学符号。

+ LaTeX数学公式符号大全：[Kapeli](https://kapeli.com/cheat_sheets/LaTeX_Math_Symbols.docset/Contents/Resources/Documents/index)

[[#颜色]]
[[#初等函数]]
[[#微积分]]
[[#线性代数]]
[[#希腊字母]]
[[#集合论]]
[[#四则运算及比较]]
[[#几何]]

---
## 一、语法

### 公式范围

单美元符号`$ $`只是单纯在所在位置显示数学公式$y=x^2+1$，双美元符号`$$ $$`标识的数学公式会另起一行并自动居中。$$y=\sum_{i=1}^{10}x$$
### 括号

大括号`{}`被预留作为LaTeX数学公式语法的括号使用，其内的公式会作为一个整体（Group）优先解释；中括号`[]`和小括号`()`没有特殊用途。下面的例子可以看出大括号对公式渲染的影响。

$$y=x_1^2$$
$$y={x_1}^2$$
### 颜色

用标识符`\color{颜色}`可以指定公式渲染的颜色，作用域从这一个颜色标识符开始到下一个颜色标识符之前结束，未指定颜色则默认为黑色。
$$\color{magenta}f(x)\color{black}=\color{red}x\color{black}+\color{green}y\color{black}+\color{blue}z$$
关键词支持的颜色如下，也可以用RGB格式指定任意颜色：`\color{rgb(r, g, b)}`
![[Pasted image 20240315103019.png]]
## 二、符号表

---
### 初等函数

+ 上标：`^`
$$y=x^2$$
+ 下标：`_`
$$y=x_1+x_2$$
+ 分式：`\frac{分子}{分母}`
$$y=\frac{1}{x}$$
+ 平方根：`\sqrt{}`
$$y=\sqrt{x}$$
+ 立方根：`\sqrt[3]{}`
$$y=\sqrt[3]{x}$$
+ 分段函数：
$$
f(x) =
\begin{cases}
    0 &  x < 0 \\
    1 &  x \geq 0
\end{cases}
$$
+ 英文表示的函数（如三角函数、对数）：`\函数名`
$$y = \sin x + \cos x + \log_2x + \ln x$$
+ 多行对齐的公式（`&`后面的内容对齐）
$$\begin{align} 
a + b & = c + d \\ 
a+b+d  &= c+2d \\ 
a+b-c &=d 
\end{align}$$

---
### 微积分

+ 极限：`\lim_{趋近情况}`
+ 无穷：`\infty`$\infty$
+ 向右箭头：`\to`$\to$
$$\lim_{x \to \infty} x$$
+ 累加：`\sum_{起始值}^{终止值}`
$$\sum_{i=1}^{10}x_i$$
+ 累乘：`\prod_{起始值}^{终止值}`
$$\prod_{i=0}^{5} x_i y_i$$
+ 积分：`\int_{积分下限}^{积分上限}`
$$\int_{0}^{\infty}\frac{1}{x+1}dx$$
+ 一阶导数：`\dot{}`$\dot{x}$
+ 二阶导数：`\ddot{}`$\ddot{x}$
+ 偏导数：`\partial`$\partial$

---
### 线性代数

+ 圆括号矩阵：
$$
\begin{pmatrix}
{a} & {b} \\ 
{c} & {d} \\ 
\end{pmatrix}
$$
+ 方括号矩阵：
$$
\begin{bmatrix}
{a} & {b} \\ 
{c} & {d} \\ 
\end{bmatrix}
$$
+ 行列式：
$$
\begin{vmatrix}
{a} & {b} \\ 
{c} & {d} \\ 
\end{vmatrix}
$$
+ 省略号：$$\dots \vdots \ddots$$
---
### 希腊字母

+ `\alpha`$\alpha$
+ `\beta`$\beta$
+ `\gamma`$\gamma$

+ `\theta`$\theta$
+ `\phi`$\phi$
+ `\varphi`$\varphi$
+ `\psi`$\psi$
+ `\omega`$\omega$

+ `\epsilon`$\epsilon$
+ `\varepsilon`$\varepsilon$
+ `\zeta`$\zeta$
+ `\xi`$\xi$

+ `\eta`$\eta$

---
### 集合论

+ 属于：`\in`$\in$ 
+ 不属于：`\notin`$\notin$
+ 包含于：`\subset`$\subset$
+ 包含：`\superset`$\supset$
+ 交集：`\cup` $\cup$
+ 并集：`\cap`$\cap$
+ 空集：`\empty`$\emptyset$

---
### 四则运算及比较

+ 乘号：`\times`$\times$
+ 除号：`\div`$\div$
+ 大于等于：`\geq`$\geq$
+ 大于等于：`\leq`$\leq$
+ 不等于：`\neq`$\neq$
+ 约等于：`\approx`$\approx$
+ 正负：`\pm`$\pm$

---
### 几何

+ 角度：`\degree`$\degree$
+ 角：`\angle`$\angle$
+ 平行：`\parallel`$\parallel$
+ 垂直：`\perp`$\perp$
+ 点乘：`\cdot` $\cdot$

---
## 其他

+ 上划线：`\overline{}`  $\overline{abc}$
+ 下划线：`\underline{}` $\underline{abc}$
+ 上波浪线：`\tilde{}` $\tilde{a}$
+ 上一横：`\bar{}` $\bar{a}$
+ 圆点：`\odot` $\odot$
+ 空格：`\quad` $\quad$
+ 非斜体：`\mathrm{}`$\mathrm{Hi}$
+ 花体：`\mathcal{}`$\mathcal{F}$
+ 黑板粗体：`\mathbb{}` $\mathbb{R}$
