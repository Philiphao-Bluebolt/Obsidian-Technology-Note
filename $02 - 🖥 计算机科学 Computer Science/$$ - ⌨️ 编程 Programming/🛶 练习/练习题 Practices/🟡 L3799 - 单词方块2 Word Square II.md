+ **链接** - [Word Squares II](https://leetcode.com/problems/word-squares-ii/)
+ **难度** - 🟡 Medium
+ **知识点** - 数组 字符串 排序 枚举

---
## 题目简介

输入四个英文单词，以上左右下的顺序返回所有可以构成如下单词方块的单词排列，要求

+ 上侧单词的首字母 = 左侧单词的首字母
+ 上侧单词的尾字母 = 右侧单词的首字母
+ 下侧单词的首字母 = 左侧单词的尾字母
+ 下侧单词的尾字母 = 右侧单词的尾字母

```
 ⚠️➡️➡️up➡️➡️⚠️
 ⬇️          ⬇️   
 ⬇️          ⬇️
left       right
 ⬇️          ⬇️
 ⬇️          ⬇️
 ⚠️➡️bottom➡️⚠️
```

---
## 解题思路

这题的解题关键是找到一个算法或者函数，可以返回已有数组元素所有可能的排列。正好Python的`itertools`标准库提供了这样一个函数——`permutations()`

+ **复杂度** - 时间 $O(n!)$ / 空间 $O(n)$ （`n`为输入数组长度）


---
## 编程问题

不熟悉Python的标准库，不知道`permutations()`函数，对枚举类型的题目经验不足。此外，没有看清楚输出要求按首字母顺序排列

---
## 知识拓展

本题中用到了枚举输入数组所有元素排列可能的Python函数，实际上，枚举排列、组合的函数也可以自己编写。




---
## 源代码留档

+ Python
`
```python
class Solution:
    def wordSquares(self, words: List[str]) -> List[List[str]]:
        
        ans = []
        for p in permutations(words, 4):
            if p[0][0] == p[1][0] and p[0][3] == p[2][0] and p[3][0] == p[1][3] and p[3][3] == p[2][3]: ans.append(p)
        ans.sort()
        return ans
```