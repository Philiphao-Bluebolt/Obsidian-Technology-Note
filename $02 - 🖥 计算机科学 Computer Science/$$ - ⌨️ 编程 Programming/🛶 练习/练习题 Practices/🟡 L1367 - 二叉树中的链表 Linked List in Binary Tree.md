
+ **链接** - [Linked List in Binary Tree](https://leetcode.com/problems/linked-list-in-binary-tree/)
+ **难度** - 🟡 Medium
+ **知识点** - 二叉树 链表 BFS

---
## 题目简介

给定一棵二叉树的根节点和一个链表的头节点，判断链表是否包含在二叉树中某段**下向道路**中

---
## 解题思路

本题本质上是树的搜索问题，可以用DFS解决（为什么不用BFS？），但由于找的是路段而不是节点，需要在已有的节点遍历算法中，嵌入一段比较路段节点的逻辑。

### 方法 - 双重DFS法

+ **复杂度** - 时间 $O(mn)$ / 空间 $O(h)=O(\log_2m)$ （`n`为输入链表长度，`m`为输入树的节点数）

使用两个DFS递归函数，第一个递归函数负责DFS遍历树的节点，寻找链表头节点值相同的节点a，第二个递归函数在找到相同节点a时启动，DFS递归比较**下向道路**的节点。

---
## 编程问题

+ 犯了一个逻辑错误，在比较链表和树**下向道路**的节点的递归函数中，只要链表遍历到尾部的空节点时就应当输出True，但是误写为只有链表和树都遍历到空节点才为True


---
## 源代码留档

### Python - 双重DFS法

```python
class Solution:
    def searchPath(self, head, root) -> bool:
        if not head or not root:
            if not head: return True
        elif head.val == root.val:
            # print(root.val, head.val)
            left = self.searchPath(head.next, root.left)
            right = self.searchPath(head.next, root.right)
            # print(root.val, head.val, left, right)
            if left or right: return True
        return False

    def isSubPath(self, head: Optional[ListNode], root: Optional[TreeNode]) -> bool:
        # Reach the end of the tree or the list is emty
        if not head or not root: return False
        
        # Start comparing sequence when the first node matches
        if root.val == head.val:
            # print(root.val, head.val)
            if self.searchPath(head, root): return True 
            
        # BFS searching the next generation
        left = self.isSubPath(head, root.left)
        right = self.isSubPath(head, root.right)
        if left or right: return True
        else: return False
```
