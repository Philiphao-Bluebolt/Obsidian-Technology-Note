+ Tutortial - [Sorting Algorithms](https://www.geeksforgeeks.org/sorting-algorithms/) 
+ Tutortial - [Searching Algorithms](https://www.geeksforgeeks.org/searching-algorithms/)

排序（Sorting）和查找（Searching）是两类常用的基本算法

| 排序算法 Sorting                | 时间复杂度 | 空间复杂度 | 内/外 | 适用于 |
| --------------------------- | ----- | ----- | --- | --- |
| [[#选择排序 Selection Sorting]] |       |       |     |     |
| [[#冒泡排序 Bubbleing Sorting]] |       |       |     |     |
| [[#插入排序 Insertion Sorting]] |       |       |     |     |
| [[#合并排序 Merge Sorting]]     |       |       |     |     |
| [[#快速排序 Quick Sorting]]     |       |       |     |     |

| 查找算法 Searching          | 时间复杂度       | 空间复杂度 | 适用于     |
| ----------------------- | ----------- | ----- | ------- |
| [[#二分查找 Binary Search]] | $O(\log n)$ |       | 已排序线性序列 |
|                         |             |       |         |

---
## 选择排序 Selection Sorting


---
## 冒泡排序 Bubbleing Sorting


---
## 插入排序 Insertion Sorting


---
## 合并排序 Merge Sorting


---
## 快速排序 Quick Sorting


---
## 二分查找 Binary Search

+ Tutorial - [Binary Search Algorithm](https://www.geeksforgeeks.org/binary-search/)

在一个**已排序**的序列中，每次只需检测正中间的元素便可将查找范围缩小一半，从而将时间复杂度降低到对数级别，这就是二分查找的基本思想，具体程序可以用递归或迭代实现。

每一次对比的中位元素序号$mid$可以由子序列的最左侧元素序号$low$和最右侧元素序号$high$计算得到，这个结论同时适用于奇偶序列。

```pseudo
mid = low + (high - low) / 2
```

#### Java

```java
int binarySearch(int arr[], int x) 
    {
        int low = 0, high = arr.length - 1;
        while (low <= high) {
            int mid = low + (high - low) / 2;

            if (arr[mid] == x) // Check if x is present at mid
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
