+ **参考**：Geeksforgeeks（[排序](https://www.geeksforgeeks.org/sorting-algorithms/) | [查找](https://www.geeksforgeeks.org/searching-algorithms/)）

排序与查找是应用于数据容器的两类基本算法，它们是很多更复杂的算法的基础，在C++、Python等语言中均有对应的标准库函数提供

+ **排序算法**：将数据容器中的元素按一定顺序重新排列
+ **查找算法**：从数据容器中找出符合要求的元素

+ **C++**：`std::sort()`
+ **Python**：`sort()`

| 类型  | 名称                                          | 时间复杂度       | 空间复杂度 | 适用于 |
| :-: | ------------------------------------------- | ----------- | ----- | --- |
| 🧩  | [[#选择排序 Selection Sorting]]                 | $O(n^2)$    |       |     |
| 🧩  | [[#冒泡排序 Bubbleing Sorting]]                 | $O(n^2)$    |       |     |
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
## 二分查找 Binary Search

+ **参考**：[Binary Search Algorithm](https://www.geeksforgeeks.org/binary-search/)
+ **复杂度**：时间 $O(\log n)$ 、空间

在一个**已排序**的序列中，每次只需检测正中间的元素便可将查找范围缩小一半，从而将时间复杂度降低到对数级别，这就是二分查找的基本思想，具体程序可以用递归或迭代实现。

每一轮迭代的中位元素序号`mid`可以由子序列的最左侧元素序号`low`和最右侧元素序号`high`通过下列式子计算得到，这个结论同时适用于奇偶序列。

```pseudo
mid = low + (high - low) / 2
```

+ **Java**

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

+ **C++**




---
## 双指针搜索 Two Pointer

+ **参考**：[Geeksforgeeks](https://www.geeksforgeeks.org/two-pointers-technique/)

双指针搜索是一种在线性容器中搜寻元素对的方法，可以将朴素搜索的时间复杂度$O(n^2)$降低到线性级别$O(n)$，其核心思想是在遍历过程中跳过的元素对。



