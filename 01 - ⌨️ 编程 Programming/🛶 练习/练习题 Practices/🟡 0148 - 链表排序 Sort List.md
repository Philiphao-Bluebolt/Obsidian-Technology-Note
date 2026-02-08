
+ **链接** - [Sort List](https://leetcode.com/problems/sort-list/)
+ **难度** - 🟡 Medium
+ **知识点** - 链表 合并排序 递归 分治法  

---
## 题目简介

对一个乱序的链表进行排序，使用的排序算法复杂度尽可能低

---
## 解题思路

所有数组的排序算法都可以用于链表，只是大部分算法的时间复杂度比较高，为了将时间复杂度降低到$O(n\log n)$，需要使用具有分治思想的合并排序。

合并排序的基本思想与二分查找类似，将一个未排序的数组拆分成前后两部分，每部分再递归拆成更小的两部分，直到每部分只有一个元素。递归拆分结束后，开始从小到大逐层合并两个已排序的部分，直到整个数组完成排序。

### 方法 - 合并排序（最优）

+ **复杂度** - 时间 $O(n\log n)$ / 空间 $O(\log n )$ （`n`为输入链表长度）

首先，需要用Floyd算法找到中位节点，然后将中位节点左右两部分的子链表头节点分别输入下一层递归函数，返回已排序好的子链表头节点。

合并左右子链表时，由于两个子链表都已排好序，只需$O(n_{left}+n_{right})$时间复杂度即可完成。

---
## 编程问题

在使用Floyd算法寻找链表中位节点时，我的写法产生了一个边缘案例：如果链表只有两个节点，快指针`fast`从`head.next`开始，慢指针`slow`从`head`开始，慢指针的上一指针从`dummy`开始，`fast`不会移动，导致慢指针的上一指针停留在`dummy`处

```
dummy -> node -> node -> None
  ^		   ^       ^
slow_prev  head   fast
		   ^
		   slow
```

正确写法是让初始`fast=head`，或者让初始`slow_prev=head`

---
## 源代码留档

### Python - 合并排序
`
```python
class Solution:
    def sortList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        
        if not head or not head.next: return head
        dummy = ListNode(0, head)

        # Find the middle node
        slow = head
        slow_prev = dummy
        fast = head
        while fast and fast.next:
            fast = fast.next.next
            slow_prev = slow
            slow = slow.next

        # Cut off the left and right halves
        slow_prev.next = None

        # Recursion 
        left = self.sortList(head)
        right = self.sortList(slow)
    
		    
        connect = dummy
        while left and right:
            if left.val < right.val:
                connect.next = left
                left = left.next
            else:
                connect.next = right
                right = right.next
            connect = connect.next
        if left: connect.next = left
        else: connect.next = right
        return dummy.next
```
