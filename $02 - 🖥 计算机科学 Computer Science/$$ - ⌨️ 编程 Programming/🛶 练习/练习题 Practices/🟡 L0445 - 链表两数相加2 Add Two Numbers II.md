
+ **链接** - [Add Two Numbers II](https://leetcode.com/problems/add-two-numbers-ii/)
+ **难度** - 🟡 Medium
+ **知识点** - 链表 

---
## 题目简介

给定两个链表，每个链表代表一个非负十进制数，链表中的每个节点代表一个数位且头节点为最高位，将两个链表代表的数字相加并以链表形式输出结果。

---
## 解题思路

由于两个数字相加时，低位会向高位进位，因此高位运算必须在低位运算完成是才能开始。但是链表的头节点为最高位，链表指针的方向与加法运算的顺序相反。容易想到，开始运算前，必须要将链表倒序。

### 方法 - 倒转法

+ **复杂度** - 时间 $O(n)$ / 空间 $O(1)$ （`n`为输入数组长度）

先将两个链表倒转，然后选择两者之间较长的链表为输出链表，数位逐位相加，最后把输出链表倒转即可。由于整个过程需要进行三次倒转操作，最好把倒转操作封装成函数。

注意有一种特殊情况是，数字的最高位进位，此时需要新建一个节点。

---
## 编程问题

+ 没有考虑数字最高位进位的特殊情况

---
## 源代码留档

### Python - 循环遍历法
`
```python
class Solution:
    def reverse(self, head: Optional[ListNode]) -> Optional[ListNode]:        
        cur = head
        cnt = 0
        prev = None
        while cur:
            nxt = cur.next
            cur.next = prev
            prev = cur
            cur = nxt
            cnt += 1
        return prev, cnt

    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        if not l1: return l2
        if not l2: return l1

        tail1, cnt1 = self.reverse(l1)
        tail2, cnt2 = self.reverse(l2)
        
        # Set the longer list as the main (output) list
        if cnt1 > cnt2: cur_main, cur_add = tail1, tail2
        else: cur_main, cur_add = tail2, tail1

        carry = False
        head = cur_main
        while cur_main:
            num = cur_main.val + int(carry)
            if cur_add: num += cur_add.val
            
            if num > 9:
                carry = True
                cur_main.val = num - 10
            else:
                carry = False
                cur_main.val = num

            if not cur_main.next: last = cur_main
            cur_main = cur_main.next
            if cur_add: cur_add = cur_add.next

        # Carry on the highest digit, creating a new node
        if carry: last.next = ListNode(1)

        return self.reverse(head)[0]
```
