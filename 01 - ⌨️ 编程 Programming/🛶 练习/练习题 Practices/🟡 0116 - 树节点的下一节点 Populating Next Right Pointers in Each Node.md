
+ **链接** - [Populating Next Right Pointers in Each Node](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)
+ **难度** - 🟡 Medium
+ **知识点** - 链表 二叉树 BFS

---
## 题目简介

给定一颗完美二叉树，树的每一个节点都有一个设计成指向右侧同层节点的指针。将所有节点的右侧指针正确设置，若右侧节点为空，则指向null

---
## 解题思路

### 方法一 - BFS

+ **复杂度** - 时间 $O(n)$ / 空间 $O(n)$ （`n`为输入树的节点个数）

问题本质上是需要把树的同一层所有节点连接成一个链表，由于是同层连接，很自然想到使用广度优先搜索，不过需要从右往左遍历。

本题规定输入二叉树为完美二叉树实际上降低了难度，因为完美二叉树的中间层不存在缺省节点，因此不需要考虑避开缺省节点。

使用Python实现时，为了提高效率，使用一个双端队列存放同一层的节点。

---
## 编程问题

+ 对BFS的遍历实现写法不熟悉
+ 对Python标准库collections的双端队列`deque`不熟悉

---
## 知识拓展

本题也可以使用深度优先搜索解决，不过效率会比较低

---
## 源代码留档

+ Python
`
```python
class Solution:
    def connect(self, root: 'Optional[Node]') -> 'Optional[Node]':
        if not root: return root
        
        q = deque([root])
        while q:
            rightNode = None
            for _ in range(len(q)):
                cur = q.popleft()
                cur.next = rightNode
                rightNode = cur
                if cur.left: q.extend((cur.right, cur.left))
        return root
```
