+ **关键词**：`for`、`while`、`do`、`break`、`continue`

C++的循环语句主要有三种，指定迭代变量的`for`语句，在开头判定的`while`语句，以及在结尾判定的`do`语句。使用循环语句时需要设定结束循环条件，避免无限循环。

在循环体之中，可以用`continue`直接跳入下一次循环，也可以用`break`跳出循环体。

+ [for 语句](#for%20语句)
+ [while 语句](#while%20语句)
+ [do语句](#do%20语句)

---
## for 语句

`for`语句需要指定继续条件，循环变量的初始化和更新表达式可以缺省，在循环体内外定义。每一次循环开始前，`for`语句先按定义的表达式自动更新循环变量的值，然后判断是否继续循环

> **普通序号遍历**

```cpp
for (int i = 0; i < arr.size(); i++){
	if (arr[i] == x) break;
	else if (arr[i] == 0) continue;
	y = arr[i];	 
}
```

> **元素遍历**

```cpp
for (int e : arr){
	if (x < e) x = e;
	y += e;
}
```

> **缺省初始化和更新表达式**

```cpp
int i = 0；
for (; i < arr.size();){
	//
	i++;
}
```

> **多个变量** - 可以在`for`语句小括号内指定多个循环变量

```cpp
for (int i = 0, j = 10; i < arr.size() && j > 3; i++, j=i/2){
	//
}
```

---
## while 语句

`while`语句是简化版的`for`语句，只需定义继续循环条件。

```cpp
int i = 0;
while (i < arr.size()){
	x += i;
	i++;
}
```

---
## do 语句

`do`语句与`while`语句类似，只是把继续循环条件的判定放在循环体最后。

```cpp
int i = 0;
do {
	x += i;
	i++;
}while(i < arr.size());
```