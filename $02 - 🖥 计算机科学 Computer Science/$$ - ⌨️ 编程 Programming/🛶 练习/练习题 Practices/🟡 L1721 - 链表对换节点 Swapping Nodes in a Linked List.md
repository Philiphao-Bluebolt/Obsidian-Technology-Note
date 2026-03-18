
+ **链接** - [Swapping Nodes in a Linked List](https://leetcode.com/problems/swapping-nodes-in-a-linked-list/)
+ **难度** - 🟡 Medium
+ **知识点** - 链表

---
## 题目简介

给定一个链表和一个位次`k`，对换链表中第`k`个和倒数第`k`个节点

---
## 解题思路

+ **复杂度** - 时间 $O(n)$ / 空间 $O(1)$ （`n`为输入链表长度）

### 寻找倒数第`k`个节点

寻找第`k`个节点很简单，但是在不知道链表长度的情况下找到倒数第`k`个节点需要一些技巧。

+ **方法一 - 测长法**：先遍历一次链表获取链表的长度，再用计数器确定倒数第`k`个节点。

+ **方法二 - 等长法（最优）**：具体做法是，在指针`cur`找到第`k`个节点的时候让另外一个指针`second`从第1个节点出发，当`cur`到达最后一个节点时，`second`到达倒数第`k`个节点。这是因为第1个节点到第`k`个节点之间的距离和倒数第`k`个节点到最后一个节点的距离相等。

### 对换节点

解决本题有两种方法，分别是对换节点对象和对换节点值，后者比较简单。

+ **方法一 - 对换节点对象**：修改前一个节点和本节点的`next`指针指向。需要在链表建立一个`dummy`节点避免交换对象为第一个节点的边缘案例。

+ **方法二 - 对换节点值**：仅修改节点值，对象指针不动。


---
## 编程问题

+ 在寻找第`k`个节点的循环中忘记给计数器加1
+ 寻找倒数第`k`个节点时，选择先遍历一次获取链表的长度，与等长法相比效率低下


---
## 源代码留档

### Python - 等长法 + 对换节点值

```python
class Solution:
    def swapNodes(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:
        if not head: return None

        cur = head
        for _ in range(1, k):
            cur = cur.next
        first = cur

        second = head
        while cur.next:
            cur = cur.next
            second = second.next
        
        first.val, second.val = second.val, first.val
        return head
```

