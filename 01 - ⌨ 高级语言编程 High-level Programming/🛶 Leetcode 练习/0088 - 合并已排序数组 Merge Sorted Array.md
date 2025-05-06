+ **链接**：[Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/description/?envType=study-plan-v2&envId=top-interview-150)

给定两个已排序数组`nums1`和`nums2`，分别有`m`和`n`个元素，将它们合并成一个排好序的数组，储存到`nums1`中。为了容纳最终结果，数组`nums1`的长度为`m+n`，后面有`n`个0

---
## 最佳解法

+ **时间复杂度**：$O(m+n)$

这个方法的核心思想是从两个数组最大的元素开始比较，每次将最大的结果复制到数组的右侧，相当于已排序的部分从右一直延申到左边

```
nums1 = [-2 0 1 4 0 0 0]
nums2 = [-1 1 6]
```

首先比较：6（`nums2`）> 4（`nums1`），6放在`nums1`的最右端

```
nums1 = [-2 0 1 4 0 0 6]
                ^	  #
nums2 = [-1 1 6]
              ^	
```

然后比较：1（`nums2`）<= 4（`nums1`），4放在`nums1`右数第二个位置

```
nums1 = [-2 0 1 4 0 4 6]
                ^	#  
nums2 = [-1 1 6]
            ^	
```

以此类推......

迭代的结束条件是`nums2`中的元素已经全部放入`nums1`中

+ C++

```c++
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        if (n == 0) return;                                          

        int p1 = m - 1;
        int p2 = n - 1;
        int ps = m + n - 1; // Insert point

        while (ps >= 0 && p2 >= 0) {
            if (p1 < 0 || nums2[p2] > nums1[p1]) {
                nums1[ps] = nums2[p2];
                ps--;
                p2--;
            }
            else {
                nums1[ps] = nums1[p1];
                ps--;
                p1--;
            }
        }
        return;
    }
};
```