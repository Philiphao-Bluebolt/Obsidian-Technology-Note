映射是一种储存键值对的数据结构，也称为**字典**（Dictionary）或**关联数组**（Associative Array），可以通过输入**键**（Key）快速查找对应的元素**值**（Value）。如果映射储存的键与值总是相同，则被称为**集合**（Set）

+ **[变体](#变体%20Varieties)** - [无序](#无序映射%20Unordered%20Map) · [有序](#有序映射%20Ordered%20Map) · [多重](#多重映射%20Multimap)
+ **[实现](#实现方法%20Implementation%20Methods)** - [哈希表](#哈希表%20Hash%20table) · [平衡二叉树](#平衡二叉树%20Balanced%20Binary%20Tree)


---
## 变体 Varieties

### 无序映射 Unordered Map

无序映射的特点是内部储存键值对的**键不能重复**，而且元素之间**没有顺序关系**，类似数学上的集合。无序映射常使用[哈希表](#哈希表%20Hash%20table)实现，其搜索操作的时间复杂度可以压缩至常数级$O(1)$，适合用于记录已经使用过的数据。




### 有序映射 Ordered Map

有序映射的特点是



### 多重映射 Multimap



---
## 实现方法 Implementation Methods


### 哈希表 Hash table

+ **参考** - [Wikipedia](https://zh.wikipedia.org/wiki/%E5%93%88%E5%B8%8C%E8%A1%A8)

哈希表也称为散列表，其工作原理与电话簿类似，通过哈希函数将键映射到一个较小的搜索范围，极大地节省了搜索时间，详见 **[哈希表](哈希表%20Hash%20Table.md)**
 




### 平衡二叉树 Balanced Binary Tree
