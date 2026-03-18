+ **链接**：[Best Time to Buy and Sell Stock III](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/description/)

给定一个记录股价的数组，每天可以买入或卖出，手上只能持有一股，**最多只允许进行两次买卖交易**，求最大收益

---
## 问题分解


### 可能交易点 

为了取得最大收益，交易点只可能位于极值点或开头、结尾

+ 买入点：可能位于极小值点或第一天
+ 卖出点：可能位于极大值点或最后一天

用一次遍历就能找到所有的可能交易点，记录在一个数组里。用正数标记卖出，负数标记买入。

### 