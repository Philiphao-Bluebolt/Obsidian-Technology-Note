
+ **链接** - [Design Front Middle Back Queue](https://leetcode.com/problems/design-front-middle-back-queue/)
+ **难度** - 🟡 Medium
+ **知识点** - 双端队列

---
## 题目简介

设计一个前、后、中间均可出入的队列容器，要求实现六个方法，分别是前端、后端、中间的弹出、压入操作。所有操作均不能超过$O(1)$复杂度

---
## 解题思路

这题的难点在于，需要实现容器中间的出入操作。

### 方法 - 双双端队列法（最优）

+ **复杂度** - 时间 $O(1)$ / 空间 $O(n)$ （`n`为输入总长度）

利用两个双端队列a和b，在每个队列中储存一半的元素，就可以对中间位置的元素进行操作。但注意，每次修改元素都需要进行一步“平衡”操作，即确保两个队列中储存的元素数量之差不超过1，一般是确保a与b储存的元素个数相等或者a比b多1

+ 前端压入：a左端压入 + 平衡
+ 后端压入：b右端压入 + 平衡
+ 中间压入：若a比b多1，a右端元素移到b左端再压入a右端
+ 前端弹出：若a非空，a左端弹出 + 平衡
+ 后端弹出：若b非空，b右端弹出 + 平衡；若b为空，a非空，a弹出
+ 中间弹出：若a非空，a有段弹出 + 平衡

---
## 编程问题

+ 没有考虑容器为空的情况
+ 中间压入操作时，没有考虑a比b多1的边缘案例
+ 不熟悉Python `and` 和 `or` 的用法

---
## 源代码留档

### Python - 双双端队列法
`
```python
class FrontMiddleBackQueue:

    def __init__(self):
        self.list_a, self.list_b = collections.deque(), collections.deque()
        # print(self.list_a, self.list_b)

    def pushFront(self, val: int) -> None:
        self.list_a.appendleft(val)
        self.balance()
        # print(self.list_a, self.list_b)

    def pushMiddle(self, val: int) -> None:
        if len(self.list_a) > len(self.list_b): self.list_b.appendleft(self.list_a.pop())
        self.list_a.append(val)
        self.balance()
        # print(self.list_a, self.list_b)

    def pushBack(self, val: int) -> None:
        self.list_b.append(val)
        self.balance()
        # print(self.list_a, self.list_b)

    def popFront(self) -> int:
        result = self.list_a.popleft() if self.list_a else -1
        self.balance()
        # print(self.list_a, self.list_b)
        return result

    def popMiddle(self) -> int:
        result = (self.list_a or [-1]).pop()
        self.balance()
        # print(self.list_a, self.list_b)
        return result

    def popBack(self) -> int:
        result = (self.list_b or self.list_a or [-1]).pop()
        self.balance()
        # print(self.list_a, self.list_b)
        return result

    def balance(self):
        if len(self.list_a) - len(self.list_b) > 1: self.list_b.appendleft(self.list_a.pop())
        if len(self.list_a) < len(self.list_b): self.list_a.append(self.list_b.popleft())
        # print(self.list_a, self.list_b)

```
