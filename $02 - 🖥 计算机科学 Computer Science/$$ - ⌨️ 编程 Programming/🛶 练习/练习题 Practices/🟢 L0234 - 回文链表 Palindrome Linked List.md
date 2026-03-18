
+ **链接** - [Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)
+ **难度** - 🟢 Easy
+ **知识点** - 链表

---
## 题目简介

判断输入链表是否回文链表，即节点的数值是否对称

---
## 解题思路

要找到一种空间复杂度为$O(1)$的方法，就不能用额外空间储存节点的值。若要用两个指针对一对节点进行逐一比较，单向链表的后半部分很难倒着回溯，所以容易想到，解题的关键是要把链表的后半部分倒序。

### 方法 - 后半倒序法

+ **复杂度** - 时间 $O(n)$ / 空间 $O(1)$ （`n`为输入链表长度）

分为三步，第一步用Floyd方法找到链表的中位节点，然后将中位节点之后链表部分倒序，最后用一对指针对节点值进行比较，直到两个指针相遇。

---
## 编程问题

+ 针对节点倒序部分的可能边缘案例想了比较久


---
## 源代码留档

### Python - 后半倒序法
`
```python
class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        if not head.next: return True

        # Find the mid node
        slow, fast = head, head
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next

        # Reverse the right half
        last_slow = slow
        slow = slow.next
        last_slow.next = None
        while slow:
            nxt = slow.next
            slow.next = last_slow
            last_slow = slow
            slow = nxt
        
        # Compare node values
        low = head
        high = last_slow
        while low and high:
            if low.val != high.val: return False
            low = low.next
            high = high.next
        else: 
            return True   
```
