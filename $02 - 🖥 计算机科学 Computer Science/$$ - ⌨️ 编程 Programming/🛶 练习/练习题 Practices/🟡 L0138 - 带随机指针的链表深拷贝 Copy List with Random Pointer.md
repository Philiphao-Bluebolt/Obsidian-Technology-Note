
+ **链接** - [Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/)
+ **难度** - 🟡 Medium
+ **知识点** - 哈希表 链表

---
## 题目简介

给定一个特殊的链表，链表的每个节点都有一个随机指针指向其他节点。对该链表进行深拷贝，要求最终得到的新链表与原链表不得有任何指针关联。

---
## 解题思路

### 方法一 - 倍增拆分法

+ **复杂度** - 时间 $O(n)$ / 空间 $O(n)$ （`n`为输入链表长度）

这个方法需要进行三次迭代

1. 拷贝迭代：将每个节点在原链表中复制一次，如`1->2->3`变为`1->1->2->2->3->3`
2. 随机指针赋值：根据原节点随机指针的指向，对每个新节点随机指针进行赋值
3. 拆分链表：将原节点和新节点拆分成两个独立链表

### 方法二 - 哈希法（最优）

+ **复杂度** - 时间 $O(n)$ / 空间 $O(n)$ （`n`为输入数组长度）

建立一个哈希表或字典，其中的键值对是原节点->新节点


---
## 编程问题

+ 一开始没有想到用哈希表实现映射
+ 犯了写错变量名的低级错误，由于Python变量无需提前声明，难以发现

---
## 源代码留档

### Python - 倍增拆分法

```python
class Solution:
    def copyRandomList(self, head: 'Optional[Node]') -> 'Optional[Node]':
        if not head: return None

        # Create new nodes at the front of each node 1->2->3 --> 1->1->2->2->3->3
        cursor = head
        while cursor:
            true_next = cursor.next
            cursor.next = Node(x = cursor.val, next = true_next)
            cursor = true_next

        # Assign the random pointer of every new nodes based on their original nodes
        cursor = head
        while cursor:
            rand = cursor.random
            cursor = cursor.next
            if rand: cursor.random = rand.next
            else: cursor.random = None
            cursor = cursor.next      

        # Depart the new nodes from the old linked list to form a new deep copy list
        cursor = head
        new_head = head.next
        cursor_2 = new_head
        while cursor:
            cursor.next = cursor.next.next
            cursor = cursor.next
            if not cursor: break
            cursor_2.next = cursor_2.next.next
            cursor_2 = cursor_2.next

        return new_head
```

### Python - 哈希法

```python
class Solution:
    def copyRandomList(self, head: 'Optional[Node]') -> 'Optional[Node]':
        if not head: return None
        
        # Create deep copy list and the hash table
        mapping = dict()
        cur = head
        new_head = Node(0)
        cur_new = new_head

        while cur:
            cur_new.next = Node(cur.val)
            cur_new = cur_new.next
            mapping.update([(cur, cur_new)])
            cur = cur.next
        new_head = new_head.next

        # Create random pointers for the new linked list
        cur = head
        cur_new = new_head
        while cur:
            if cur.random: cur_new.random = mapping[cur.random]
            else: cur_new.random = None
            cur_new = cur_new.next
            cur = cur.next

        return new_head 
            
```