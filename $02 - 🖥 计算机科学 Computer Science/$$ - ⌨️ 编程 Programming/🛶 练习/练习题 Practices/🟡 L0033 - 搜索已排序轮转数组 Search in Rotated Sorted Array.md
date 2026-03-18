
+ **链接** - [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)
+ **难度** - 🟡 Medium
+ **知识点** - 二分查找 数组

---
## 题目简介

给定一个已排序但是进行了轮转操作的数组，在对数复杂度下查找指定元素，（原数组严格单增）

---
## 解题思路

数组进行了轮转操作后不再是一个已排序的数组，看似并不能使用二分查找。但轮转排序数组的特殊性质使得本题依然可以使用二分查找解决，只是缩小范围的条件逻辑需要稍作修改。

### 方法 - 特殊二分查找

+ **复杂度** - 时间 $O(\log(n))$ / 空间 $O(1)$ （`n`为输入数组长度）

我们观察被轮转的已排序数组，可以发现数组分为两个已排序的部分，称为“前尾”和“后首”，前尾部分的元素总是后首部分的元素大。而通过比较搜寻目标和当前搜寻范围的中位元素值、尾元素值即可以确定目标在前半还是后半部分。二分查找的终止条件仍旧是尾指针越过首指针。

+ 当前搜寻范围内四种情况：
	+ 如果中位元素比尾元素大，说明中位元素位于前尾部分
		+ 如果目标值位于中位元素值与尾元素值之间，则在左半部分
		+ 否则在右半部分
	+ 如果中位元素比尾元素小，说明中位元素位于后首部分
		+ 如果目标值位于中位元素值与尾元素值之间，则在右半部分
		+ 否则在左半部分

---
## 编程问题

+ 编写二分查找的条件逻辑时，忽略了目标即为当前尾元素的情况，没有用`<= >=`

---
## 源代码留档

### Python - 特殊二分查找
`
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        if len(nums) == 0: return -1

        low = 0
        high = len(nums) - 1

        while low <= high:
            mid = low + (high - low) // 2
            if nums[mid] == target: return mid

            # At front
            if nums[mid] > nums[high]:        
                if target <= nums[high] or target > nums[mid]:
                    low = mid + 1
                else:
                    high = mid - 1
            else:
                if nums[mid] < target <= nums[high]:
                    low = mid + 1
                else:
                    high = mid - 1
        return -1
```
