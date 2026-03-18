
+ **链接** - [Design HashSet](https://leetcode.com/problems/design-hashset/)
+ **难度** - 🟢 Easy
+ **知识点** - 哈希表 哈希函数 链表

---
## 题目简介

设计一个哈希表，实现键的插入、删除、检测功能，且时间复杂度不能超过常数级$O(1)$

---
## 解题思路

+ **复杂度** - 时间 $O(1)$ / 空间 $O(n)$ （`n`为储存元素个数）

设计哈希表的关键在于哈希函数的设计。设计优良的哈希函数应当将输入键空间较为平均地映射到不同的哈希值。针对不同的输入键数据类型有不同的哈希函数设计。

考虑到本题输入的键是非负整型数字，可以使用求余运算作为哈希函数，根据运算得到的余数将输入键映射到一个数组的不同位置。同时，为避免哈希值冲突，数组的位置需要储存一个链表头指针而非元素，链表的每一个节点储存的是同一映射值的不同键值。

---
## 编程问题


---
## 知识拓展

参见[哈希函数 Hash Function](哈希函数%20Hash%20Function.md)

---
## 源代码留档

### Python - 循环遍历法
`
```python
class ListNode:
    def __init__(self, key=0, next=None):
        self.key = key
        self.next = next

class MyHashSet:
    def __init__(self):
        self.cap = 100000
        self.bucket = [None] * self.cap

    def add(self, key: int) -> None:
        head = self.hashing(key)
        last = None
        while head:
            if head.key == key: return
            if head and not head.next: last = head
            head = head.next
        if last: last.next = ListNode(key)
        else: self.bucket[key % self.cap] = ListNode(key)
        return

    def remove(self, key: int) -> None:
        head = self.hashing(key)
        prev = None
        while head:
            if head.key == key: 
                if prev: prev.next = head.next
                else: self.bucket[key % self.cap] = head.next
                return
            prev = head
            head = head.next
        return

    def contains(self, key: int) -> bool:
        head = self.hashing(key)
        while head:
            if head.key == key: return True
            head = head.next   
        return False

    def hashing(self, key: int) -> Optional[ListNode]:
        return self.bucket[key % self.cap]

```
