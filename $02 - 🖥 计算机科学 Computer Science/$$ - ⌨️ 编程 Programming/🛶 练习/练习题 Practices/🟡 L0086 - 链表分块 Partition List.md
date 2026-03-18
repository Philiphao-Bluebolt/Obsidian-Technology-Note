
+ **链接** - [Partition List](https://leetcode.com/problems/partition-list/)
+ **难度** - 🟡 Medium
+ **知识点** - 链表

---
## 题目简介

给定一个链表和一个数字`x`，将链表所有值小于数字`x`的节点移到链表的前端，值大于等于数字`x`的节点移到链表的后端，且不能改变这两组节点内部的顺序。

---
## 解题思路

这题的思路不难，但容易犯逻辑错误

### 方法一 - 前移重连法

+ **复杂度** - 时间 $O(n)$ / 空间 $O(1)$ （`n`为输入链表长度）

先创建一个假节点作为链表的开头，然后创建一个连接指针`cur_connect`，移动到链表第一个大于等于数字`x`的节点之前。

创建一个遍历指针`cur`和上一节点指针`last_cur`，向前移动，在遇到`cur_connect`之前不做任何操作；遇到`cur_connect`之后的每一个小于`x`的节点，将其从原位置分离并连接到`cur_connect`的下一位置，直到链表结尾。


### 方法二 - 



---
## 编程问题

+ 编写遍历链表的`while`语句时，检测空指针的条件不小心写到了比较节点值的条件之后，造成条件语句尝试访问空节点的节点值

---
## 源代码留档

### Python
`
```python
class Solution:
    def partition(self, head: Optional[ListNode], x: int) -> Optional[ListNode]:
        if not head or not head.next: return head

        dummy = ListNode(0, head)
        cur_connect = dummy

        while cur_connect.next and cur_connect.next.val < x:
            cur_connect = cur_connect.next

        last_cur = dummy
        cur = head
        start_cut = False
        while cur:
            if cur == cur_connect.next and not start_cut: 
                start_cut = True
            if start_cut is True and cur.val < x:
                nxt_connect = cur_connect.next
                cur_connect.next = cur
                nxt = cur.next
                cur.next = nxt_connect
                last_cur.next = cur = nxt
                cur_connect = cur_connect.next
            else:
                last_cur = cur
                cur = cur.next                   
        return dummy.next
```
