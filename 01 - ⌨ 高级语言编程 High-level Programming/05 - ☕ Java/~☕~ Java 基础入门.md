+ 教程 - [https://www.w3schools.com/java/](https://www.w3schools.com/java/)

Java的变量与语法规则和C++十分相似，变量需要声明，语句块用大括号`{}`表示，且基本变量声明、条件语句、循环语句的写法相同，因此，熟悉C++的初学者可以快速上手Java。

Java属于强面向对象语言，包括程序入口在内的所有代码都必须定义在类中。

1. **变量 Variable**
	+ [[#基本类型 Basic Types]]
	+ [[#引用 Reference]]
	+ [[#数组 Array]]
		+ [[#静态数组 Static Array]]
		+ [[#动态数组 Dynamic Array]]
		+ [[#二维数组 2D Array]]
	+ [[#字符串 String]]
	+ [[#类型转换 Type Conversion]]
2. **语法语句 Syntax**
	+ [[#条件 Condition]]
	+ [[#循环 Loop]]
3. **类与对象 Class & Object**
	+ [[#方法 Method]]
	+ [[#修饰符 Modifier]]
4. **包和文件 Package & File**
5. **其他**
	+ [[#命令行调试 Command Line Debug]]
	+ [[#常用函数 Useful Functions]]
		+ [[#数学函数]]
	+ [[#常用数据容器 Container]]

---
## 基本类型 Basic Types

Java有八种基本变量类型，它们有以下共性：

+ 储存**真实数值**而非引用地址
+ 储存在**栈**中而非堆中
+ 有对应的**类**形式

| Type      | Size    | Range/Values                                    | Example                  |
| --------- | ------- | ----------------------------------------------- | ------------------------ |
| `byte`    | 8 bits  | -128 to 127                                     | `byte b = 100;`          |
| `short`   | 16 bits | -32,768 to 32,767                               | `short s = 1000;`        |
| `int`     | 32 bits | -2^31 to 2^31 - 1                               | `int i = 100000;`        |
| `long`    | 64 bits | -2^63 to 2^63 - 1                               | `long l = 10000000000L;` |
| `float`   | 32 bits | Approximately 7 decimal digits                  | `float f = 3.14f;`       |
| `double`  | 64 bits | Approximately 15 decimal digits                 | `double d = 3.14159;`    |
| `char`    | 16 bits | Single character or Unicode value (0 to 65,535) | `char c = 'A';`          |
| `boolean` | 1 bit   | `true` or `false`                               | `boolean flag = true;`   |

### ⭕注意

+ Java不支持布尔值`boolean`自动转换为数值0和1，需要使用三元运算`flag ? 1 : 0`手动转换，相反，也不支持数值直接转换为布尔值
+ Java的字符只能用单引号`''`表示，双引号表示的是字符串


---
## 引用 Reference

 Java所有**非基本类型**的实例（包括对象、数组、字符串）都使用引用（Reference）表示，因此一般情况下使用对象或数组的名称赋值或传参时都属于**浅拷贝**——只是多创建了一个指向同一对象的引用，并没有真正创建一个新的对象。
 
```java
import java.util.Arrays;

int[] a = {1, 2, 4, 6, 5};

/* 浅拷贝（a和b指向同一数组） */
int[] b = a;

/* 深拷贝（创建了一个新数组b） */
int[] b = Arrays.copyOf(a, a.length);
```

 Java的引用和C++的指针作用极为相似，两者本质上都是一个指向变量或对象的地址，只是引用的值不能像指针一样随意通过数学运算改变。

Java非基本类型的创建可以拆分成两部分——声明引用和赋值

```java
ListNode l1 = new ListNode();

ListNode l1;
l1 = new ListNode();
```

### ⭕注意

+ 由于引用本质上是地址，以引用名作为参数传入函数时属于浅拷贝，在函数内部修改这个传入的参数时会导致原实例（典型如数组）发生改变。这个特性与C++指针传参类似

---
## 数组 Array

Java同时提供长度固定的静态数组和长度可变的动态数组

| 类型   | 长度可变 | 访问速度 | 内存分配 | 内存位置 |
| ---- | ---- | ---- | ---- | ---- |
| 静态数组 | 否    | 快    | 连续   | 栈    |
| 动态数组 | 是    | 慢    | 任意   | 堆    |

### 静态数组 Static Array

为静态数组分配的内存空间是栈中的连续地址，因此静态数组长度不可变而访问速度较快。

```java
import java.util.Arrays;

/* 声明 */
String[] words = {"love", "water", "fire", "rose"}; //赋值
int[] nums = new int[6]; //不赋值

/* 获取长度 */
len = words.length;

/* 读写元素 */
get_word = words[1];
words[2] = "ice" 

/* 转成动态列表 */
List<String> dynamic_words = Arrays.asList(words);

```

### 动态数组 Dynamic Array

Java的动态数组由类`ArrayList`实现。动态数组的元素在堆中占用的内存空间彼此之间是独立的，因此动态数组的长度可以扩充，缺点是访问速度慢。

```java
import java.util.ArrayList;
import java.util.Arrays;

/* 声明 */
ArrayList<String> words = new ArrayList<String>(); //不赋值
ArrayList<Integer> nums = new ArrayList<Integer>(Arrays.asList(1, 2, 3)); //赋值

/* 添加元素 */
words.add("love");
words.add("water");
words.add("fire");
words.add(1, "rose"); // 指定位置插入

/* 获取长度 */
len = words.size();

/* 读写元素 */
get_word = words.get(1);
words.set(2, "ice");

/* 删除元素 */
words.remove(0); //指定序号
dynamicArray.remove(String.valueOf("rose")); //指定元素内容

```

### 二维数组 2D Array

二维数组通过嵌套定义“数组的数组”实现

```java
import java.util.ArrayList;

/* 静态实现 */
int[][] nums = {{},{},{}};

/* 动态实现 */
ArrayList<ArrayList<Integer>> nums = new ArrayList<Integer>(); 

/* 动态套静态实现 */
ArrayList<int[]> nums = new ArrayList();
```

### ⭕注意

+ 动态数组`ArrayList`不接受基本变量类型，要使用基本变量类型对应的类形式，如`int`-->`Integer`
+ Java数组的变量名是引用


---
## 字符串 String

Java字符串的用法和C++类似，与Python一样支持加号连接

```java
String str = "Hello World";

/* 获取长度 */
int len = str.length();

/* 读取单个字符 */
char get_char = str.charAt(2);

/* 提取子串 */
String sub = str.substring(4, 7); // 注意实际上是4~6

/* 连接字符串 */
str_r = str + str;

```

此外，字符串内部实现了不少方法用于字符串处理。注意，所有写入型的方法都返回一个修改后的字符串。

| 方法            | 示例                      | 返回         | 用途                       |
| ------------- | ----------------------- | :--------- | ------------------------ |
| `replace()`   | `str.replace('l', 'w')` | `String`   | 替换指定字符                   |
| `trim()`      | `str.trim()`            | `String`   | 除去字符串**首尾**的多余空格         |
| `substring()` | `str.substring(4, 7)`   | `String`   | 返回子串，不包括尾编号              |
| `contains()`  | `str.contain("Hello")`  | `boolean`  | 判断是否含有指定的子串              |
| `indexOf()`   | `str.indexOf("")`       | `int`      | 返回字符或子串第一次出现的序号，未出现则返回-1 |
| `split()`     | `str.split("[s]")`      | `String[]` | 以正则表达式规定的符号对字符串进行分割      |

### ⭕注意

+ Java的字符串内容是不可修改的，因此所有修改字符串的方法（如`trim()`、`replace()`）实际上是创建了一个新的字符串，而非直接对原字符串进行修改。
+ 基于上述原因，虽然字符串传入函数内是引用传参，函数内部对这个字符串的修改并不会改变原字符串。

---
## 类型转换 Type Conversion

Java的有些类型转换可以在表达式中自动转换，有些则只能通过函数转换

### 自动转换

+ `int` --> `char`

```java
int num = 47;
char ch = num;
char ch2 = ch + 3;
```

+ `char` --> `int`

```java
char ch = '';

```

### 手动转换

|    原类型     |     新类型     |                      使用的方法                      |
| :--------: | :---------: | :---------------------------------------------: |
|  `Type[]`  | `ArrayList` | `ArrayList<Type> arr_list = Arrays.asList(arr)` |
|   `int`    |  `String`   |    `String num_str = Integer.toString(num)`     |
|   `char`   |  `String`   |    `String ch_str = Character.toString(ch)`     |
|   `char`   |    `int`    |    `int num = Character.getNumericValue(ch)`    |
| `String[]` |  `String`   | `String join_arr = String.join(", ", str_arr)`  |
|  `String`  |    `int`    |        `int num = Integer.parseInt(str)`        |

---
## 条件 Condition

Java支持`if else`和`switch`两种条件语句，与C++一样

```java
switch(index)
{
	case 0:
		...
		break;
	case 1:
		...
		break;
	default:
		...
		break;
}
```


---
## 循环 Loop

Java有四种循环语句，分别是：

+ `for` - 指定迭代循环
+ `for each` - 线性容器遍历
+ `while` - “当”型循环
+ `do` - “直到”型循环

这里只列出Java特有的`for each`循环，其他三种循环与C++一致

```java
String str = "Hello World";
int[][] mat = {{1, 2},{3, 4}};

for (char i : str) {}
for (int[] row : mat) {}
```


---
## 方法 Method 

Java的所有代码都在类中实现，因此理论上所有的Java函数都是类的成员函数（方法）



---
## 修饰符 Modifier




---
## 命令行调试 Command Line Debug

### 输出 Output 

```java
/* 换行输出 */
System.out.println("Hello World");

/* 标准输出 */
System.out.printf();

```




---
## 常用函数 Useful Functions

这里列出Java的常用函数

### 数学函数




---
## 常用数据容器 Container

