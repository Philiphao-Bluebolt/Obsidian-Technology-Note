+ **关键词**：`if`、`else`、`switch`、`case`、`break`

C++的条件语句用于构建分支控制流结构，包括二分的“if...else”，多分支单值的“switch...case”，以及赋值常用的三目运算符。

+ [if 语句](#if%20语句)
+ [switch 语句](#switch%20语句)
+ [三目运算符](#三目运算符)

---
## if 语句

`if`语句是最基础的二分条件判断语句。

> **普通写法** - `else if`本质上是两个嵌套的`if`语句，用于构建多分支结构

```C++
if (x > 0){
	y = x;
	return y;
}
else if (x < 0){
	y = -x;
	return y;
}
else return x;
```

> **单行写法** - 分支内只有一个语句时可以省略大括号，与`if`语句写在同一行

```C++
if (x >= 0) return x;
else return -x;
```

> **带初始化写法**（C++17）

```C++
if (int i = my_fun(); i > 0){
	return true;
}
else{
	return false;
}
```

---
## switch 语句

`switch`语句是多分支单值判断语句。其运行逻辑是，跳到第一个设定常值与输入变量`x`值相等的`case`语句处继续执行，因此`switch`语句有分支穿透性。

> **一般写法** - 用`break`避免分支穿透

```C++
switch (pooltoy){
	case "Cerisey":
		cout << "Ride!";
		break;
	case "Kinyo":
		cout << "Snuggle!";
		break;
	default:
		cout << "Squeak!";
		break;
}
```

> **穿透性**  - 如果没有遇到`break`或`return`，在跳入位置以下所有分支的语句都会被执行。以下例子中，`case 1`往下的所有语句均会执行

```C++
int x = 1;
switch (x){
	case 0:
		x = x + 1；
	case 1:
		x = x - 1;
	case 2:
		x = -x;
	default:
		x = -1;
}
cout << x; // x = -1
```

> **多取值合并** - `case`的进入条件只能是单个常量，不能设定为范围。这种情况下可以利用穿透性合并多个`case`

```C++
switch (x){
	case 0:
	case 1:
	case 2:
		return x;
	case -1:
	case -2:
		return -x;
}
```

> **带初始化写法**（C++17）

```C++
switch (int i = my_fun()){
	case 0:
		return false;
	case 1:
		return true;
	}
```


---
## 三目运算符

三目运算符是二分条件赋值的一种简化写法

```C++
var = x > 0 ? x+1 : x/2;
```

等价写法如下

```C++
if (x > 0) var = x + 1;
else var = x / 2;
```