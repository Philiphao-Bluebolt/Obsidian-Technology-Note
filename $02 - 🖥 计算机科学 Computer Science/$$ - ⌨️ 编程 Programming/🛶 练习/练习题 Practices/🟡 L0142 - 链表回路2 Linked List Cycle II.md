+ **链接** - [Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)
+ **难度** - 🟡 Medium
+ **知识点** - 链表 Floyd算法 数论

---
## 题目简介

给定一个链表，判断链表是否存在回路结构，若有，返回链表回路的第一个节点

---
## 解题思路

### 方法 - Floyd算法

+ **复杂度** - 时间 $O(n)$ / 空间 $O(1)$ （`n`为输入链表长度）

使用快慢指针的Floyd算法专门解决链表回路问题，一个快指针和一个慢指针同时从头节点出发，若快指针和慢指针相遇，表明链表存在回路。

确认链表回路的第一个节点需要一定的数学推算。结论是，快慢节点相遇处和头节点到第一个回路节点的距离相等。具体的数学证明请见：[链表/Floyd算法](链表%20Linked%20List.md#Floyd算法)

---
## 编程问题

+ 实现时，不小心将Floyd算法的判断快慢指针的语句写在指针前进的语句之前，运行时刚进入循环就跳入回路计数逻辑


---
## 源代码留档

### Python - Floyd算法

```python
class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if not head: return None

        fast = head
        slow = head
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next
            if fast == slow: 
                while head != slow:
                    slow = slow.next
                    head = head.next
                return slow
```