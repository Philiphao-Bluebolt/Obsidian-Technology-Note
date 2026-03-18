+ **链接**：[Longest Arithmetic Subsequence of Given Difference](https://leetcode.com/problems/longest-arithmetic-subsequence-of-given-difference/description/)

给定一个数列`arr`和一个指定差值`d`，求等差值为指定差值`d`的最长子数列长度，子数列是从原数列取走某些元素形成的序列

---
## 字典遍历法 

+ 时间复杂度：$O(n)$

遍历整个数列，用一个字典记录以每一个在数列出现过的数字结尾的符合要求的子序列最大长度，如果它符合要求的前一项在之前出现过，就把长度+1然后记下来。

+ 举例：数列157853421、逐差值-2
	+ 第一步：1的前一项应为-1，但是-1没有出现过，因此记录下以1结尾的最长子序列长度为1
	+ 第二步：5的前一项应为3，同样没有出现过，以5结尾最长为1
	+ 第三步：7的前一项应为5，5出现过且以5结尾最长为1，因此以7结尾的最长子序列长度为2
	+ ……
	+ 最终结果，整个数列符合要求的最长子序列长度为4，以1结尾（7531）

由于只需要求符合要求的子数列长度，并不需要记录子数列的具体值。

```C++
class Solution {
public:
    int longestSubsequence(vector<int>& arr, int difference) {
        
        unordered_map<int, int> dp;
        int longest = 1;

        for (int i = 0; i < arr.size(); i++) {
            dp[arr[i]] = dp[arr[i] - difference] + 1;
            if (longest < dp[arr[i]]) longest = dp[arr[i]];
        }
  
        return longest;
    }
};
```

---
## 递归法

+ 时间复杂度：$O(n)$

