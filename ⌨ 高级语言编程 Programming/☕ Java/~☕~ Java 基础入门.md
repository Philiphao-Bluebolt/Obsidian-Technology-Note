Java的变量与语法规则和C++十分相似，比如说，变量需要声明，语句块用大括号`{}`表示，基本变量声明、条件语句、循环语句的写法相同，因此，熟悉C++的初学者可以快速上手Java。

Java属于强面向对象语言，包括程序入口在内的所有代码都必须定义在类中。

+ 变量类型
	+ [[#基本类型]]
	+ [[#数组]]
		+ [[#静态数组]]
		+ [[#动态数组]]
		+ [[#二维数组]]
	+ [[#字符串]]
	+ [[#引用]]
+ 语法语句
+ 类与对象
+ 命令行调试
	+ [[#命令行输出]]
	+ [[#命令行输入]]
+ 包和文件

---
## 基本类型

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
## 数组

Java同时提供长度固定的静态数组和长度可变的动态数组

| 类型   | 长度可变 | 访问速度 | 内存分配 | 内存位置 |
| ---- | ---- | ---- | ---- | ---- |
| 静态数组 | 否    | 快    | 连续   | 栈    |
| 动态数组 | 是    | 慢    | 任意   | 堆    |

### 静态数组

为静态数组分配的内存空间是栈中的连续地址，因此静态数组长度不可变而访问速度较快。

```java
/* 声明 */
String[] words = {"love", "water", "fire", "rose"}; //赋值
int[] nums = new int[6]; //不赋值

/* 获取长度 */
len = words.length;

/* 读写元素 */
get_word = words[1];
words[2] = "ice" 

```

### 动态数组

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

### 二维数组

二维数组通过嵌套定义“数组的数组”实现

```java
import java.util.ArrayList;

/* 静态实现 */
int[][] nums = {{},{},{}};

/* 动态实现 */
ArrayList<ArrayList<Integer>> nums = new ArrayList<Integer>(); 

/* 动态套静态实现 */
ArrayList<int[]> nums = new ArrayList<>()
```



### ⭕注意

+ 动态数组`ArrayList`不接受基本变量类型，要使用基本变量类型对应的类形式，如`int`-->`Integer`
+ Java数组的变量名是地址引用，与对象类似


---
## 字符串

Java字符串的用法和C++类似

```java
String str = "Hello World";

/* 获取长度 */
int len = str.length();

/* 读取单个字符 */
char get_char = str.charAt(2);

/* 提取子串 */
String sub = str.substring(4, 7); // 注意实际上是4~6

/* 替换指定字符或子串 */
str.replace('l', 'w') // l -> w

```



---
## 引用

 Java所有**非基本类型**的实例（包括对象、数组、字符串）都使用引用表示，因此一般情况下使用对象或数组的名称赋值或传参时都属于**浅拷贝**——只是多创建了一个指向同一对象的引用，并没有真正创建一个新的对象。
 
```java
import java.util.Arrays;

int[] a = {1, 2, 4, 6, 5};

/* 浅拷贝（a和b指向同一数组） */
int[] b = a;

/* 深拷贝（创建了一个新数组b） */
int[] b = Arrays.copyOf(a, a.length);
```

 Java的引用和C++的指针作用极为相似，两者都是指向一个变量或对象的地址，只是引用的值不能向指针一样随意通过运算改变。

Java非基本类型的创建可以拆分成两部分——声明引用和赋值

```java
ListNode l1 = new ListNode();

ListNode l1;
l1 = new ListNode();
```

---
## 函数方法

Java的所有代码都在类中实现，因此理论上所有的Java函数都是类的成员函数（方法）





---
## 命令行输出

```java
/* 换行输出 */
System.out.println("Hello World");

```

---
## 命令行输入



