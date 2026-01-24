
+ **链接** - [Convert Sorted List to Binary Search Tree](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/)
+ **难度** - 🟡 Medium
+ **知识点** - 链表 二叉树 递归 分治法

---
## 题目简介

将一个已排列好的链表变换为一颗平衡二叉搜索树

---
## 解题思路

实际上，平衡二叉搜索树的构建原理和数组的二分查找思想是类似的，都借用了分形递归的思想，本质上都是需要找到中位节点，然后将中位节点的左右部分分别传送给下一层递归，直到所有链表节点都成为树的一部分。

在寻找中位节点时，可以使用**龟兔算法**。

+ **复杂度** - 时间 $O(n\lg n)$ / 空间 $O(\lg n)$ （`n`为输入链表长度）

---
## 编程问题

本题有一个很容易忽略的操作，在每层递归里，把左右链表段的首指针传给下一层递归时，右段链表不需要任何操作，但是左段链表必须**断开与中位节点的链接**，否则会把整段链表传给左子树，导致无穷递归。

---
## 知识拓展

+ 二叉搜索树：每一个节点的左子节点不大于根节点，右子节点不小于根节点的二叉树
+ 平衡树：任意一个节点的左右子树深度之差不超过1。

---
## 源代码留档

+ Python

```python
class Solution:
    def sortedListToBST(self, head: Optional[ListNode]) -> Optional[TreeNode]:
        if not head: return None
        if not head.next: return TreeNode(head.val)
        
        fast = head
        slow = head
        while fast and fast.next:
            slow_prev = slow
            slow = slow.next
            fast = fast.next.next
        
        slow_prev.next = None
        root = TreeNode(slow.val, self.sortedListToBST(head), self.sortedListToBST(slow.next))
        return root
        
```