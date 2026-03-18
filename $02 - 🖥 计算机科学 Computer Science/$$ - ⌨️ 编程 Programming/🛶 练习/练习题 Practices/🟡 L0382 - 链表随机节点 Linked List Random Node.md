+ **链接** - [Linked List Random Node](https://leetcode.com/problems/linked-list-random-node/)
+ **难度** - 🟡 Medium
+ **知识点** - 链表 随机 水塘抽样算法

---
## 题目简介

给定一个非常长的链表，编写一个函数实现随机输出链表中一个节点值，且每个节点被选中的几率相同。限定时间复杂度不能超过$O(n)$，空间复杂度不能超过$O(1)$


---
## 解题思路

本题考察的算法称为水塘抽样算法，这是一种专门针对长度未知的样本进行滑动等概率采样的算法。由于假定输入链表的长度非常长，不能通过遍历预先确定链表的长度，只能边遍历边采样

### 最优方法 - 水塘抽样算法

初始输出设置为`null`，正常遍历链表，对于第`i`个节点，有`1/i`的概率将输出值替换为该节点值。容易证明，每个节点被抽到的几率均等。

---
## 编程问题

+ 对Python的随机库函数不熟悉，不知道`random.randint()`函数的取值范围是左右皆闭


---
## 源代码留档

### Python - 水塘抽样算法
`
```python
class Solution:
    def __init__(self, head: Optional[ListNode]):
        self.head = head

    def getRandom(self) -> int:
        ans = None
        cur = self.head
        i = 1
        while cur:
            if random.randint(1, i) == i: ans = cur.val   
            i += 1
            cur = cur.next
        return ans
```
