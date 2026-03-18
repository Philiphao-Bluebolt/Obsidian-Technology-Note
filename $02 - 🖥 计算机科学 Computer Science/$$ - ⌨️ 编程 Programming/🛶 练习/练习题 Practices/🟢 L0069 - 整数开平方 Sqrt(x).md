+ **链接** - [Sqrt(x)](https://leetcode.com/problems/sqrtx/)
+ **难度** - 🟢 Easy
+ **知识点** - 二分查找

---
## 题目简介

给定一个整数，求其开平方向下取整的结果

---
## 解题思路

### 方法 - 二分查找

+ **复杂度** - 时间 $O(\log n)$ / 空间 $O(1)$ （`n`为输入的整数）

求整数开平方的向下取整结果，相当于求一个平方数不大于给定整数的最大整数，而我们知道一个整数的开平方小于等于其自身，因此我们的搜索范围为`0~n`

利用二分查找即可快速找到符合要求的结果。


---
## 源代码留档

### Python - 循环遍历法
`
```python
class Solution:
    def mySqrt(self, x: int) -> int:
        
        low = 0
        high = x
        while low <= high:
            mid = low + (high - low) // 2
            squ = mid**2
            squp = (mid+1)**2

            if squ <= x: 
                if squp > x: return mid
                else: low = mid+1
            else: 
                high = mid - 1
```
