序列（Sequence）是一种**抽象**的抽象数据结构，也被称为数组、列表、元组、向量。序列中的数据以一定**次序**连续排列，允许**指定序号**读取、删除任意元素，或在任意位置插入元素。

+ **[实现方法](#实现方法%20Implementation%20Methods)** - [静态数组](#静态数组%20Static%20Array) · [动态数组](#动态数组%20Dynamic%20Array) · [链表](#链表%20Linked%20List) · [平衡二叉树](#平衡二叉树%20Balanced%20Binary%20Tree)
+ **[操作算法](#操作算法%20Algorithm%20of%20Actions)** - [访问](#访问%20Access) · [插入](#插入%20Insert) · [删除](#删除%20Delete) · [排序](#排序%20Sort) · [搜索](#搜索%20Search)

---
## 实现方法 Implementation Methods

序列常见的实现方式包括静态数组、动态数组、链表、平衡二叉树。链表牺牲访问速度换取删插速度。平衡二叉树可以将序列元素的平均搜索时间复杂度控制在对数级。

主流编程语言提供的序列容器或定义语法：

+ **C** 
	+ `var[]`（静态数组）
	+ `malloc`（可定义动态数组）
+ **C++** 
	+ `vector`（动态数组）
	+ `list`（链表）
	+ `array`（静态数组）
+ **Python**
	+ `list` - `[]`（列表，即动态数组）
	+ `tuple` - `()`（元组，即只读静态数组）
+ **Java**
	+ `var[]`（静态数组）
	+ `ArrayList`（动态数组）

### 静态数组 Static Array

序列最简单的实现方法是使用一段连续的内存储存元素，以这种方式实现的序列常称为数组（Array）或静态数组（Static Array）。这种方法的主要缺点是无法更改序列的长度，不适用于需要频繁增删元素的场合。

+ **C** - `int arr[3] = {5, 1, 4}`
+ **C++** -  `std::array<int, 3> arr = {5, 1, 4}`
+ **Python** - `arr = (5, 1, 4)`
+ **Java** - `int[] arr = {5, 1, 4}`

### 动态数组 Dynamic Array

动态数组在长度超过当前内存块的最大限制时会进行内存重分配（Memory Reallocating），将原来的元素转移到一块更大的连续内存，并释放原有的内存块。C++的向量（Vector）、Python的列表（List）是动态数组

+ **C++** -  `std::vector<int> arr = {5, 1, 4}`
+ **Python** - `arr = [5, 1, 4]`
+ **Java** - `ArrayList<Integer> nums = new ArrayList<Integer>(Arrays.asList(5, 1, 4))`

### 链表 Linked List

链表是一种离散化的序列实现方法，储存元素的内存地址之间并不相邻，而每一个元素节点都额外储存一个指向下一个元素节点的指针。详见[**链表**](链表%20Linked%20List.md)一页

+ **C++** - `std::list`

### 平衡二叉树 Balanced Binary Tree




---
## 操作算法 Algorithm of Actions

序列的常见操作包括访问、插入、删除、排序、搜索等。

### 访问 Access


### 插入 Insert


### 删除 Delete


### 排序 Sort


### 搜索 Search