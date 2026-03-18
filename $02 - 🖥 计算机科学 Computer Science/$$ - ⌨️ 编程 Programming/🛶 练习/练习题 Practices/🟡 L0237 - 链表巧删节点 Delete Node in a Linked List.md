
+ **链接** - [Delete Node in a Linked List](https://leetcode.com/problems/delete-node-in-a-linked-list/)
+ **难度** - 🟡 Medium
+ **知识点** - 链表

---
## 题目简介

给定一个**头节点未知**的链表，要求删去输入指针指向的节点（该节点不为尾节点）

---
## 解题思路

本题属于脑筋急转弯，要在未知头节点未知的条件下删去指定节点，意味着该节点前一节点的下一指针无法修改，只能通过修改节点值的方法等效“删除”节点

### 方法 - 跳马法

+ **复杂度** - 时间 $O(1)$ / 空间 $O(1)$ 

将目标节点的值改为下一节点的值，然后下一指针改为指向下下节点，相当于物理上删除了下一个节点，而目标节点成为原本的下一个节点。

仅需两行代码即可解决：

```cpp
class Solution {
public:
    void deleteNode(ListNode* node) {
        node->val = node->next->val;
        node->next = node->next->next;
    }
};
```

---
## 编程问题

+ 最初的解法是将目标节点之后的所有节点的值前移，删除尾节点。与最优解比较明显较为繁琐

