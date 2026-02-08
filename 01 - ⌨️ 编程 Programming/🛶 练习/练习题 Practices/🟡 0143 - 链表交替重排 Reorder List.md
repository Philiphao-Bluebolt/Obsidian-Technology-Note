
+ **链接** - [Reorder List](https://leetcode.com/problems/reorder-list/)
+ **难度** - 🟡 Medium
+ **知识点** - 链表 栈 Floyd算法 递归 

---
## 题目简介

给定一个链表，对其节点对折交替顺序进行重排，即进行如下变换

`1->2->3->4->5->6` 

变为

`1->6->2->5->3->4`

---
## 解题思路

这题的难点在于找到一种时间复杂度为时间 $O(n)$ / 空间 $O(1)$ 的算法解决问题。直观上，将尾部的节点按倒序插入头部的节点之中的操作需要$O(n^2)$的时间复杂度，因为链表无法从后往前遍历。

突破点：既然链表不能从后往前遍历，我们就将链表倒序。

### 方法 - 后半倒序法

+ **复杂度** - 时间 $O(n)$ / 空间 $O(1)$ （`n`为输入链表长度）

分析重排规则可以发现，只有后半部分的节点需要倒序访问，因此我们的算法可以分为三步

1. 找到中间节点，将链表分割成前后两部分 - Floyd算法
2. 将链表的后半部分倒序
3. 前后两部分同时遍历，将尾部的节点依次插入前半部分的两个节点之间

---
## 编程问题

+ 实现倒序的时候循环的逻辑出了点小问题，没有在更新当前指针`cur`之前更新上一指针`last_cur`的值




---
## 源代码留档

### Python - 后半倒序法
`
```python
class Solution:
    def reorderList(self, head: Optional[ListNode]) -> None:
        """
        Do not return anything, modify head in-place instead.
        """
        if not head or not head.next or not head.next.next: return

        # Find the mid node
        slow, fast = head, head.next
        while fast.next:
            if not fast.next.next: fast = fast.next
            else: fast = fast.next.next
            slow = slow.next

        # Reverse the right half
        cur = slow.next
        last_cur = None
        slow.next = None
        while cur:
            temp = cur.next
            cur.next = last_cur
            if temp is None: break
            last_cur = cur
            cur = temp

        # Create the new linked list
        lead = head
        while cur:
            temp = lead.next
            lead.next = cur
            temp2 = cur.next
            cur.next = temp
            lead = temp
            cur = temp2
        return
```

