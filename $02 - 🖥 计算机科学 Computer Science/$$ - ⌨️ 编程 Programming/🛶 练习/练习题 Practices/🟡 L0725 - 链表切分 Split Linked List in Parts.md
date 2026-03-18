
+ **链接** - [Split Linked List in Parts](https://leetcode.com/problems/split-linked-list-in-parts/)
+ **难度** - 🟡 Medium
+ **知识点** - 链表 除法分配

---
## 题目简介

将给定的链表均匀切分成`k`份，“均匀”的意思是每一分块分到的节点数之差最大不能超过1，且分配较多的分块排列在前面

---
## 解题思路

本题其实是简单的除法分配问题。设链表长度为`n`，考虑到`n`并不总是能被`k`除尽，余数部分将分配给前几个分块，也就是说，若余数为3，则前3个分块分配到的节点数+1。

### 方法

+ **复杂度** - 时间 $O(n)$ / 空间 $O(1)$ （`n`为输入链表长度）

首先遍历一遍链表以确认链表的长度`n`，然后计算`k`个分块每份分到的节点数。每个节点至少能分到`n//k`个节点，而前`n%k`个节点则额外多分配一个节点。

接下来是遍历链表，需要使用一个计数器计算当前分块已分到的节点数，当计数器达到应分配节点数时，断开当前节点的下一指针，当计数器归零时，将当前节点指针存入输出数组的对应分块中。

---
## 编程问题

+ 在切分链表的遍历逻辑中，没有考虑每份只有一个节点的边缘案例
+ 没有考虑`n%k`个节点之后无节点的边缘案例，导致输出数组过短

---
## 源代码留档

### Python
`
```python
class Solution:
    def splitListToParts(self, head: Optional[ListNode], k: int) -> List[Optional[ListNode]]:
        if not head: return [None] * k
        if k == 0: return None

        # Get length
        cur, size = head, 0
        while cur:
            size += 1
            cur = cur.next

        # 
        base = size // k
        extraIndex = size % k

        print(base, extraIndex)
        ans = []
        cur = head
        cnt = 1
        index = 0 
        while cur: 
            if cnt >= base + int(index < extraIndex):
                if cnt == 1: ans.append(cur)
                nxt = cur.next
                cur.next = None
                cur = nxt
                cnt = 1
                index += 1
            else:
                if cnt == 1:
                    ans.append(cur)
                cur = cur.next
                cnt += 1
        while index < k:
            ans.append(None)
            index += 1
        return ans
```
