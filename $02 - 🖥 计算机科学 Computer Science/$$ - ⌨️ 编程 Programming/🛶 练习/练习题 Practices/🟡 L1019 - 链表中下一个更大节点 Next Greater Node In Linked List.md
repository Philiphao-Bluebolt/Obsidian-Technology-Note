
+ **链接** - [Next Greater Node In Linked List](https://leetcode.com/problems/next-greater-node-in-linked-list/)
+ **难度** - 🟡 Medium
+ **知识点** - 链表 数组 栈

---
## 题目简介

对链表里的每一个节点，检测该节点之后数值比该节点大的第一个节点，若该节点之后没有数值更大的节点，输出0。结果以数组的形式输出。

---
## 解题思路

如果对每个节点都用暴力搜索解决，则时间复杂度会上升到$O(n^2)$，这不是一个可行的方法。实际上，如果借用一部分额外储存空间，只需遍历一次链表即可寻得所有节点的下一个最大节点。

### 方法 - 栈记法

+ **复杂度** - 时间 $O(n)$ / 空间 $O(n)$ （`n`为输入链表长度）

这个方法可以概括成一句话：用一个栈储存未找到“下一更大节点”的节点，当遇到更大节点时，节点出栈。

首先，需要将链表转存为数组，这是因为只有数组才能以$O(1)$时间复杂度指定序号访问任意元素，这一步对后面比较数值大小的操作至关重要。

然后开始遍历数组，遍历逻辑如下：

+ 若当前节点的值大于栈顶节点，则栈顶节点出栈并记录当前节点为其下一个更大节点；连续出栈直到栈顶元素的值不小于当前节点
+ 当前节点入栈

---
## 编程问题

+ 误以为`list.reverse()`有返回值， 实际上该函数仅操作列表本身而无返回值
+ 对枚举函数`enumerate()`的用法不熟，该函数返回

---
## 源代码留档

### Python - 栈记法
`
```python
class Solution:
    def nextLargerNodes(self, head: Optional[ListNode]) -> List[int]:
        
        if not head: return None
		
		# Linked list -> array
        arr = []
        while head:
            arr.append(head.val)
            head = head.next
        
        # Iterate the array
        ans = [0] * len(arr)
        stack = []
        for i, val in enumerate(arr):
            while stack and arr[stack[-1]] < val:
                ans[stack.pop()] = val
            stack.append(i)
            
        return ans
```
