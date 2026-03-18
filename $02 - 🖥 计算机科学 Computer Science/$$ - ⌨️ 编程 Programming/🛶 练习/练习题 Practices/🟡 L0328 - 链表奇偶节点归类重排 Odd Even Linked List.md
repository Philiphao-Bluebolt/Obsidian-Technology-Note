
+ **链接** - [Odd Even Linked List](https://leetcode.com/problems/odd-even-linked-list/)
+ **难度** - 🟡 Medium
+ **知识点** - 链表

---
## 题目简介

给定一个链表，将奇数位次的节点（1、3、5……）全部移到链表前，偶数位次的节点（2、4、6……）全部移到链表后，且不改变奇节点、偶节点内部之间各自原本排序。

---
## 解题思路

考虑到奇偶节点是交替排列的，只要把每个奇节点的前向指针移到下一个偶节点之后，再交替把每个偶节点的前向指针移到下一个奇节点之后，最后把最后一个奇节点的前向指针指向第一个偶节点，就能实现重排。

### 方法 - 交替跳跃法

+ **复杂度** - 时间 $O(n)$ / 空间 $O(1)$ （`n`为输入链表长度）

首先排除两种边缘案例，链表为空或者长度为一的情况。

创建一个奇指针指向头节点，即第一个节点；一个偶指针指向第二个节点。遍历时，每次交替将节点的前向指针跳跃一位。结束遍历的条件是当前偶节点或当前偶节点的下一个节点为null

```
1 -> 2 -> 3 -> 4 -> 5 -> 6 -> ...
1.next = 2.next
1 = 1.next(3)
2.next = 3.next
...

```


---
## 编程问题

在设计遍历链表的逻辑时，没有想到怎么判断最后一个节点是奇节点还是偶节点，当时想到用一个比特位记录节点的奇偶性，但这种方法比较冗余而且容易出错。正确方法是使用两个指针，这样自然而然就能记录最后一个节点的奇偶性。

---
## 源代码留档

### Python - 交替跳跃法
`
```python
class Solution:
    def oddEvenList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if not head or not head.next: return head

        odd = head
        even_head = even = head.next

        while even and even.next:
            odd.next = even.next
            odd = odd.next
            even.next = odd.next
            even = even.next
            
        odd.next = even_head
        return head
```
