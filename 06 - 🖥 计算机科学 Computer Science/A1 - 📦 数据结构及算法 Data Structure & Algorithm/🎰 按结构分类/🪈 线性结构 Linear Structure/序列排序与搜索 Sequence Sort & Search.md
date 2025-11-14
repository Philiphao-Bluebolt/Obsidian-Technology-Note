+ **参考**：Geeksforgeeks（[排序](https://www.geeksforgeeks.org/sorting-algorithms/) | [查找](https://www.geeksforgeeks.org/searching-algorithms/)）

排序与查找是应用于数据容器的两类基本算法，它们是很多更复杂的算法的基础，在C++、Python等语言中均有对应的标准库函数提供

+ **排序算法**：将数据容器中的元素按一定顺序重新排列
+ **查找算法**：从数据容器中找出符合要求的元素

+ **C++**：`std::sort()`
+ **Python**：`sort()`

外排序、内排序、稳定排序、不稳定排序


| 类型  | 名称                                          | 时间复杂度       | 空间复杂度 | 适用于 |
| :-: | ------------------------------------------- | ----------- | ----- | --- |
| 🧩  | [[#选择排序]]                                   | $O(n^2)$    |       |     |
| 🧩  | [[#冒泡排序]]                                   | $O(n^2)$    |       |     |
| 🧩  | [[#插入排序 Insertion Sorting]]                 |             |       |     |
| 🧩  | [[#合并排序 Merge Sorting]]                     |             |       |     |
| 🧩  | [[#快速排序 Quick Sorting]]                     |             |       |     |
| 🔎  | [[#二分查找 Binary Search]]                     | $O(\log n)$ |       |     |
| 🔎  | [双指针搜索 Two Pointer](#双指针搜索%20Two%20Pointer) | $O(n)$      |       |     |
| 🔎  |                                             |             |       |     |
| 🔎  |                                             |             |       |     |
| 🔎  |                                             |             |       |     |





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

每一轮迭代的中位元素序号`mid`可以由子序列的最左侧元素序号`low`和最右侧元素序号`high`取平均得到。子序列长度为奇数时`mid`指向中间元素，为偶数时指向中间靠左元素（整型去尾）。

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