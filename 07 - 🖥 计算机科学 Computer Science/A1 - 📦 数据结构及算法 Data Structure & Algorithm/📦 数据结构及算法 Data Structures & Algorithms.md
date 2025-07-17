+ **参考**：[Geeksforgeeks](https://www.geeksforgeeks.org/dsa-tutorial-learn-data-structures-and-algorithms/)

**数据结构**描述了计算机储存、组织数据的几何形式，常见的数据结构包括数组、链表、栈、队列、树、图等；**算法**则描述对数据结构中的元素进行操作的方法，常见的数据结构操作包括插入、删除、清空、排序、搜索、寻路、复制等。

抽象数据结构和对应的容器实现有一定区别。**抽象数据结构**从原理上定义了数据组织结构与操作形式，**容器**则是抽象数据结构在编程语言中的封装，在编译层面可能以另一种数据结构的形式运行。

+ 🗃 **数据结构**
	+ 线性：栈 · 队列 · 双端队列 · 数组 · 链表 · 双向链表
	+ 关联：字典 · 
	+ 哈希：哈希表 · 
	+ 树：二叉 · 堆
	+ 图：有向 · 有向无环
+ 🛠 **操作算法**
	+ 排序：选择 · 冒泡 · 插入 · 快速 · 堆 · 希尔 · 归并 · 桶 · 梳
	+ 搜索：[顺序](#顺序搜索%20Sequential%20Search) · **[二分](#二分搜索%20Binary%20Search)** · 双指针 · [DFS](#深度优先搜索%20Depth-first%20Search) · [BFS](#广度优先搜索%20Breadth-first%20Search)
	+ 寻路：Dijkstra · 

---
## 栈 Stack

+ **参考**：

栈是一种遵循**先入后出**（FILO）原则的线性数据结构，其储存原理类似盒子或者箱子：最先放入的元素被压在栈的底端，而最后放入的元素位于栈的顶端，只有栈的顶端元素才能被移除。栈的基本操作包括压入元素、弹出顶端元素、访问指定元素的值。

+ 栈的容器实现
	+ C++：由标准库`<stack>`引入的`std::stack`
	+ Python：
	+ Java：


---
## 队列 Queue






---
## 选择排序 Selection Sorting

+ **参考**：





---
## 冒泡排序 Bubbleing Sorting


---
## 插入排序 Insertion Sorting


---
## 合并排序 Merge Sorting


---
## 快速排序 Quick Sorting



---
## 堆排序 Heap Sort

+ **参考**：[Geeksforgeeks](https://www.geeksforgeeks.org/heap-sort/)
+ **类型**：
+ **复杂度**：时间 $O()$ - 空间 $O()$


---
## 顺序搜索 Sequential Search

+ **复杂度**：时间 $O(n)$ - 空间 $O(1)$

顺序搜索是针对线性容器最简单的搜索方法，即从第一个元素搜索到最后一个元素，最坏情况下的时间复杂度为线性复杂度$O(n)$

### 实现代码

> **C++**

```C++
int seqSearch(vector<int>& nums, int target) {
	for (int i = 0; i < nums.size(); i++) {
		if (nums[i] == target) return i;
	}
	return -1;
}
```

---
## 二分搜索 Binary Search

+ **参考**：[Geeksforgeeks](https://www.geeksforgeeks.org/binary-search/)
+ **复杂度**：时间 $O(\log n)$ - 空间 $O(1)$

二分搜索又称为折半搜索，其基本思想是：在一个**已排序**的序列中，每次只需检测正中间的元素便可将查找范围缩小一半，从而将时间复杂度降低到对数级别，是线性结构查找算法中效率最高的算法。

每一轮迭代的中位元素序号`mid`可以由子序列的最左侧元素序号`low`和最右侧元素序号`high`取平均得到。子序列长度为奇数时`mid`指向中间元素，为偶数时指向中间靠左元素。

```C++
mid = (low + high) / 2

// oddArr = [1, 2, 3], mid = 2
// evenArr = [1, 2, 3, 4], mid = 2
```

继续迭代的条件需要取等号，否则在两边的指针重叠时会忽略指向值

```C++
while (low <= high)
```

### 实现代码

> **C++**

```C++
int binarySearch(vector<int>& nums, int target) {

    int left = 0, right = nums.size() - 1, mid = 0;
    while (left <= right) {
        mid = (left + right) / 2;
        if (target < nums[mid]) right = mid - 1;
        else if (target > nums[mid]) left = mid + 1;
        else return mid;
    }
	return -1;
}
```

> **Java**

```java
int binarySearch(int arr[], int x) 
    {
        int low = 0, high = arr.length - 1;
        while (low <= high) {
            int mid = low + (high - low) / 2;

            if (arr[mid] == x) // Check if x is at mid
                return mid;

            if (arr[mid] < x) // If x greater, ignore left half
                low = mid + 1;

            else // If x is smaller, ignore right half
                high = mid - 1;
        }

        // If we reach here, then element was not present
        return -1;
    }
```


---
## 双指针搜索 Two Pointer Search

+ **参考**：[Geeksforgeeks](https://www.geeksforgeeks.org/two-pointers-technique/)
+ **复杂度**：时间 $O(n)$ - 空间 $O(1)$

双指针搜索是一种在已排序的线性容器中搜寻元素对的方法，可以将搜索两个元素的时间复杂度降低到线性级别$O(n)$，其基本思想是在遍历过程中跳过的元素对。

---
## 深度优先搜索 Depth-first Search




---
## 广度优先搜索 Breadth-first Search