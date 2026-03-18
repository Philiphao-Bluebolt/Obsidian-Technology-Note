
+ **链接** - [Remove Duplicates from Sorted List II](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/)
+ **难度** - 🟡 Medium
+ **知识点** - 链表 双指针

---
## 题目简介

给定一个已排序的链表，删除所有出现过重复的节点

---
## 解题思路

+ **复杂度** - 时间 $O(n)$ / 空间 $O(1)$ （`n`为输入链表长度）

这题的解决方法很简单，直接遍历一次链表，在检测到下一个节点与本节点数值重复时，留置一个指针在上一个节点，跳过所有有重复的部分。难点在于循环内逻辑的控制，以及边缘测试用例比较复杂。

这题的边缘测试用例有下面几种情况：

+ 空链表 / 链表长度为一
+ 重复部分位于链表头：需要接出来一个假首节点
+ 重复部分位于链表尾：注意不要尝试访问空节点的值

---
## 编程问题

没有充分考虑边缘测试用例——重复部分位于链表尾，导致没有完全通过测试


---
## 知识拓展





---
## 源代码留档

+ Python
`
```python
class Solution:
    def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if head is None or head.next is None: return head

        cursor = head
        dummy = ListNode(0, head)
        last_cursor = dummy
        dup = False
        while cursor.next is not None:
            if dup is False:
                if cursor.next.val == cursor.val: dup = True
                else: last_cursor = cursor
            else:
                if cursor.next.val != cursor.val: 
                    last_cursor.next = cursor.next
                    dup = False
            cursor = cursor.next
        
        if dup is True: last_cursor.next = None
        return dummy.next
```