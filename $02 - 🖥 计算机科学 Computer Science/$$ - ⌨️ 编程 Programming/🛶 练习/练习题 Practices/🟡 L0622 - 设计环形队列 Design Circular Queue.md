
+ **链接** - [Design Circular Queue](https://leetcode.com/problems/design-circular-queue/)
+ **难度** - 🟡 Medium
+ **知识点** - 队列 链表 环形寄存器 

---
## 题目简介

编写一个类实现指定容量的FIFO队列数据结构，需要实现删插、读取队头队尾元素、检测空队列或满队列等操作。要求所有类方法的时间和空间复杂度都为常数

---
## 解题思路

与实现栈相比，实现队列数据结构的难点在于先入先出的逻辑实现，这种输入输出形式使得队头压入和队尾弹出操作在空间上都会让指针向前移动。如果使用连续内存区域储存队列，队列元素在不断压入弹出操作之后会触及内存区域的右界，最终会越界；如果使用数组实现队列，则每次在队头插入元素都需要线性时间复杂度。

### 方法一 - 链表实现

+ **复杂度** - 时间 $O(1)$ / 空间 $O(1)$ （`n`为输入长度）

链表的节点采取分立储存策略，没有连续内存空间的大小限制，适合用于实现容量不定的队列。链表的头节点作为队头，尾节点作为队尾，插入元素时在队尾新建一个节点，删除元素时在队头删除一个节点。

### 方法二 - 环形寄存器实现（最优解）

+ **复杂度** - 时间 $O(1)$ / 空间 $O(1)$ （`n`为输入数组长度）

在队列容量固定的条件下，环形寄存器是实现队列的最优工具。实际编程时，环形寄存器使用静态



---
## 编程问题

+ 使用链表实现，在编写插入元素的函数时，没有正确理解链式赋值的运行原理，从而产生了循环链表。

+ 一开始的想法是用循环链表实现，但发现逻辑上不太直观，而且在队列容量为1时会产生边缘案例，每个函数对容量为1的边缘案例都需要特殊处理，造成代码逻辑复杂且可读性差。

---
## 源代码留档

### Python - 链表实现
`
```python
class ListNode:
    def __init__(self, val = 0, next = None):
        self.val = val
        self.next = next

class MyCircularQueue:

    def __init__(self, k: int):
        self.maxSize = k
        self.size = 0
        self.head = None
        self.tail = None
    
    def enQueue(self, value: int) -> bool:
        if self.isFull(): return False
        else:
            if self.isEmpty(): 
                self.head = ListNode(value)
                self.tail = self.head
            else:
                self.tail.next = ListNode(value)
                self.tail = self.tail.next
            self.size += 1
            return True

    def deQueue(self) -> bool:
        if self.isEmpty(): return False
        else:
            self.head = self.head.next
            self.size -= 1
            return True

    def Front(self) -> int:
        return -1 if self.isEmpty() else self.head.val

    def Rear(self) -> int:
        return -1 if self.isEmpty() else self.tail.val

    def isEmpty(self) -> bool:
        return self.size == 0

    def isFull(self) -> bool:
        return self.maxSize == self.size
```
