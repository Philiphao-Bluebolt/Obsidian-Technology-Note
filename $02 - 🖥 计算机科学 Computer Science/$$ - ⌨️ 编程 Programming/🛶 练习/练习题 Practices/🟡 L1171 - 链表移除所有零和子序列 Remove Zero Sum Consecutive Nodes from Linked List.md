
+ **链接** - [Remove Zero Sum Consecutive Nodes from Linked List](https://leetcode.com/problems/remove-zero-sum-consecutive-nodes-from-linked-list/)
+ **难度** - 🟡 Medium
+ **知识点** - 链表 前项和 哈希表

---
## 题目简介

给定一个链表，删除链表中所有和为零的子序列（如链表 `4 2 -3 1 3` 中的子序列 `2 -3 1`），使最终的链表不包含任何和为零的子序列

---
## 解题思路

### 方法 - 前项和哈希法

+ **复杂度** - 时间 $O(n)$ / 空间 $O(n)$ （`n`为输入链表长度）

考虑到问题描述涉及到子序列的和，很容易想到用前项和方法求解，如果链表某个位置出现的前项和与前面重复，则说明这两个位置之间的数和为零。

举例，链表 `4 2 -3 1 3`的前项和序列为`4 6 3 4 7`，出现了两个`4`，说明第一个前项和为`4`的元素之后到当前节点的序列元素和为零，节点应全部移除。此外，有一种边缘案例需要考虑，也就是和为零的子序列包含第一个元素的情况，此时会出现值为零的前项和，因此需要在链表前先建立一个假节点。

为记录之前出现过的前项和，需要建立一个哈希表，以前项和值作为键，节点指针作为值。

遍历链表的逻辑如下：

+ 若当前节点的前项和没有出现过，将当前前项和及节点指针计入哈希表
+ 若当前节点的前项和出现过，从之前出现相同前项和的节点开始算，它的下一个节点一直到当前节点都要被删除。

---
## 编程问题

+ 删除节点部分的逻辑出现了一些问题，通过插桩排除操作。

---
## 源代码留档

### Python - 前项和哈希法

```python
class Solution:
    def removeZeroSumSublists(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if not head: return None

        # Preparations
        dummy = ListNode(0, head)
        prefix_sum = 0
        hashing = {0: dummy}

        cur = head
        while cur:
            prefix_sum += cur.val
            if prefix_sum in hashing:
                del_first = hashing[prefix_sum]
                last_cur = cur
                cur = cur.next
                del_cur = del_first.next
                del_first.next = cur
                temp_sum = prefix_sum
                while del_cur != last_cur:
                    temp_sum += del_cur.val
                    # print(temp_sum)
                    hashing.pop(temp_sum)
                    del_cur = del_cur.next
            else:
                hashing.update({prefix_sum: cur})
                cur = cur.next
        return dummy.next
```
