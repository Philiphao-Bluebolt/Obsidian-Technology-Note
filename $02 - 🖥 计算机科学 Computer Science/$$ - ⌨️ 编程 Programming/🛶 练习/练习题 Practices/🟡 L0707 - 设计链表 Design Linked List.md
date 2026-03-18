+ **链接** - [Design Linked List](https://leetcode.com/problems/design-linked-list/)
+ **难度** - 🟡 Medium
+ **知识点** - 链表

---
## 题目简介

以类的形式实现一个功能完整的链表，必要功能包括头部插入节点、尾部插入节点、指定位次删插节点、指定位次读取节点

---
## 解题思路

本题考察链表的遍历，难度不大，但容易犯逻辑错误。

---
## 编程问题

编写方法时犯了两个逻辑错误

+ 在头部插入节点时，新建节点的下一指针应当指向原头节点，但误写成指向头节点的下一节点
+ 在任意位置删除节点时，没有考虑删除头部节点的特殊边缘案例

---
## 源代码留档

### Python - 循环遍历法
`
```python
class ListNode:
    def __init__(self, val: int = 0, next: Optional[ListNode] = None):
        self.val = val
        self.next = next

class MyLinkedList:

    def __init__(self):
        # self.nodeDict = dict() # Index -> Node pointer
        self.head = None

    def get(self, index: int) -> int:
        # self.test()
        cur = self.head
        cnt = 0
        while cur:
            if cnt == index: return cur.val
            cur = cur.next
            cnt += 1
        return -1

    def addAtHead(self, val: int) -> None:
        # self.test()
        if not self.head: self.head = ListNode(val)
        else:
            nxt = self.head
            self.head = ListNode(val, nxt)
        return

    def addAtTail(self, val: int) -> None:
        # self.test()
        if not self.head: self.head = ListNode(val)
        else:
            cur = self.head
            while cur.next: cur = cur.next
            cur.next = ListNode(val)

    def addAtIndex(self, index: int, val: int) -> None:
        # self.test()
        if index == 0: self.addAtHead(val)
        else:
            cur = self.head
            cnt = 0
            while cur:
                if cnt == index: 
                    prev.next = ListNode(val, cur)
                    return
                prev = cur
                cur = cur.next
                cnt += 1
            else: 
                if cnt == index: 
                    prev.next = ListNode(val)
            return
                
    def deleteAtIndex(self, index: int) -> None:
        # self.test()
        cur = self.head
        cnt = 0
        prev = None
        while cur:
            if cnt == index:
                if prev: prev.next = cur.next
                else: self.head = self.head.next
                return
            prev = cur
            cnt += 1
            cur = cur.next
        return

    def test(self):
        cur = self.head
        while cur:
            print(cur.val, end=' ')
            cur = cur.next
        print("\n")
        return
```
