
---
## 注释

```cpp
//Single Line

/*
Multi Line
*/
```

---
## 变量和运算

C++的变量需要声明以分配内存地址，声明后类型不可改变；运算可以用`++`表示将当前值加一

```cpp
int a = 1, b = 2;
string str = "Hello World";

a = pow(b, a);
b++; //b += 1
```


---
## 分支

C++可以用`switch-case`语句表示多分支

```cpp
if (x < 1 && y > 2 || z != 0)
{
	//pass
}
else if (w == 1)
{
	//pass
}
else
{
	//pass
}
```

```cpp
switch(i)
{
	case 0:
		//fork1
	case 1:
		//fork2
	default:
		//default
}
```

---
## 循环

```cpp
for (int i = 0; i < 10; i++)
{
	//pass
}
```

---
## 类

```cpp
class 
```

---
## 程序入口

C++的程序必须从`main()`函数开始执行

```cpp
int main()
{
	//pass
}
```