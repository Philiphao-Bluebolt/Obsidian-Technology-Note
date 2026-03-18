
+ **链接** - [LRU Cache](https://leetcode.com/problems/lru-cache/)
+ **难度** - 🟡 Medium
+ **知识点** - 双端链表 哈希表 假节点法

---
## 题目简介

编写一个类模拟实现缓存的最近最少使用算法（翻译历史遗留问题，其实应该翻译成**最久未用**），即给定缓存的最大容量，当缓存已满而需要加入新数据时，淘汰最久没有访问或更新的数据。具体而言，需要实现LRU缓存的数据访问和插入，且两种操作必须在常数时间复杂度$O(1)$下完成。

---
## 解题思路

+ **参考** - 

本题是难得一见的精题，考察的编程和算法知识范围相当广。

为了实现题目要求，算法需要用到两种数据结构，双端链表和哈希表。哈希表用来实现常数访问复杂度，而双端链表则用来记录数据从最近访问到最久未用的顺序。具体实现是，用一个哈希表储存所有链表数据节点的指针。

这里使用双端链表是为了在移动中间的数据节点时，可以在常数复杂度下将被移动节点的前后节点接回去。

实现双端链表时需要在一头一尾加上两个假节点`oldest`和`lastest`，否则每次改动数据节点的位置都需要额外考虑前后节点为`None`的边缘案例以防止越界。

数据节点必须包含`key`，否则在删除数据时无法通过链表访问数据对应的`key`，无法将节点从哈希表中删除。

---
## 编程问题

+ 代码有很多冗余和复杂化的操作，比如判断键值对是否存在的条件`key in cache`写成了`cache.get(key)`；
+ 更新数据节点值的时候，误更新哈希表中的节点指针而非实际节点的值
+ 相比例程，没有做到将节点的增添和删除分离成两个独立函数，还没有学会用面向对象的思路解决问题。

---
## 知识拓展

+ LRU算法是最常用的缓存置换算法之一，除此之外，还有LFU、NMRU等算法。

---
## 源代码留档

### Python - nitts的较优写法

```python
class Node:
    def __init__(self, key, val):
        self.key = key
        self.val = val
        self.prev = None
        self.next = None

class LRUCache:

    def __init__(self, capacity: int):
        self.cap = capacity
        self.cache = {}

        self.oldest = Node(0, 0)
        self.latest = Node(0, 0)
        self.oldest.next = self.latest
        self.latest.prev = self.oldest
        

    def get(self, key: int) -> int:
        if key in self.cache:
            self.remove(self.cache[key])
            self.insert(self.cache[key])
            return self.cache[key].val
        return -1

    def remove(self, node):
        prev, next = node.prev, node.next
        prev.next = next
        next.prev = prev
    
    def insert(self, node):
        prev, next = self.latest.prev, self.latest
        prev.next = next.prev = node
        node.next = next
        node.prev = prev

    def put(self, key: int, value: int) -> None:
        if key in self.cache:
            self.remove(self.cache[key])
        self.cache[key] = Node(key, value)
        self.insert(self.cache[key])

        if len(self.cache) > self.cap:
            lru = self.oldest.next
            self.remove(lru)
            del self.cache[lru.key]
```

### Python - 我的写法
`
```python
class ListNode:
    def __init__(self, key: int = 0, value: int = 0):
        self.key = key
        self.value = value
        self.next = None
        self.prev = None

class LRUCache:

    def __init__(self, capacity: int):
        self.cap = capacity
        self.cnt = 0
        self.oldest, self.lastest = ListNode(), ListNode()
        self.oldest.next = self.lastest
        self.lastest.prev = self.oldest
        self.cache = dict()

    def get(self, key: int) -> int:
        if not self.cache.get(key): return -1 # Key not found

        node = self.cache.get(key)
        self.renew(node)
        return node.value

    def put(self, key: int, value: int) -> None:
        # Key already exists - only update the node value
        if self.cache.get(key):
            node = self.cache.get(key)
            node.value = value
        else:
            # Delete the oldest node when the cache is full
            if self.cnt == self.cap:
                # Delete from linked list
                outdated_node = self.oldest.next
                new_oldest = outdated_node.next
                self.oldest.next = new_oldest
                new_oldest.prev = self.oldest

                # Delete from hash table
                self.cache.pop(outdated_node.key)

            # Normal counting
            else: self.cnt += 1
            
            node = ListNode(key, value)
            self.cache.update({key: node})

        # Renew the node and update the hash table
        self.renew(node)
        return

    def renew(self, node: ListNode) -> None:
        
        # Depart the old node from the original spot 
        if node.next: 
            node.next.prev = node.prev
            node.prev.next = node.next
    
        node.prev = self.lastest.prev
        node.next = self.lastest
        self.lastest.prev.next = node
        self.lastest.prev = node
        return
```

