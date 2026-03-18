
+ **链接** - [Design Authentication Manager](https://leetcode.com/problems/design-authentication-manager/)
+ **难度** - 🟡 Medium
+ **知识点** - 双端链表 哈希表

---
## 题目简介

设计一个验证码管理系统，实现下面几个功能：

+ 预设一个验证码有效时长
+ 在某一指定时间生成一个验证码
+ 在某一指定时间刷新一个未过期的验证码
+ 在某一指定时间查询有效验证码的数量

---
## 解题思路

### 方法 - 双端链表 + 哈希表

+ **复杂度** - 时间 $O(n)$ / 空间 $O(n)$ （`n`为输入内容长度）

分析题目需求，可以发现几个要点：验证码的总数不确定；刷新操作需要快速访问一个指定的验证码；而查询有效验证码一个比较快的方法则需要将验证码按生成或刷新时长排列，且需要频繁修改排列顺寻。快速访问指定验证码可以用哈希表实现，而总数不定的顺序排列以及快速删插操作则需要使用双端链表。

首先设置一个假节点，每生成一个新的验证码，就新建一个节点，记录验证码的代码和创建时间，同时以验证码代码为键，节点指针为值存入哈希表；而刷新验证码时，则将验证码的创建时间修改为输入时间，然后将节点移动到链表头（假节点之后）；这样就能确保验证码在链表中按从新到旧的顺序排列。

查询操作则是从头节电开始遍历直到遇到第一个过期验证码节点，`O(n)`时间复杂度


---
## 编程问题

+ 使用双端链表时，经常忘记更新节点的前向指针`prev`
+ 设计逻辑时，误将刚好达到有效时长的验证码判定为有效，实际上按照题目意思应该是无效

---
## 源代码留档

### Python - 双端链表 + 哈希表
`
```python
class TokenNode:
    def __init__(self, tokenId: str = "", createTime: int = 0, next: Optional[TokenNode] = None, last: Optional[TokenNode] = None):
        self.tokenId = tokenId
        self.createTime = createTime
        self.next = next
        self.last = last

class AuthenticationManager:
    def __init__(self, timeToLive: int):
        self.time_limit = timeToLive
        self.dummy = TokenNode()
        self.hash = dict()

    def generate(self, tokenId: str, currentTime: int) -> None:
        nxt = self.dummy.next
        newNode = TokenNode(tokenId, currentTime, nxt, self.dummy)
        if nxt: nxt.last = newNode
        self.dummy.next = newNode
        self.hash.update({tokenId: newNode})

    def renew(self, tokenId: str, currentTime: int) -> None:

        if not (tokenId in self.hash): return         
        node = self.hash[tokenId]
        if currentTime - node.createTime >= self.time_limit: return
        else:
            node.createTime = currentTime
            node.last.next = node.next
            if node.next: node.next.last = node.last
            self.dummy.next, node.next, node.last = node, self.dummy.next, self.dummy
            if node.next: node.next.last = node

    def countUnexpiredTokens(self, currentTime: int) -> int:
        # cur = self.dummy.next
        # while cur:
        #     print(cur.tokenId, cur.createTime)
        #     cur = cur.next
        cnt = 0
        cur = self.dummy.next
        while cur and currentTime - cur.createTime < self.time_limit:
            cnt += 1
            cur = cur.next
        return cnt

```