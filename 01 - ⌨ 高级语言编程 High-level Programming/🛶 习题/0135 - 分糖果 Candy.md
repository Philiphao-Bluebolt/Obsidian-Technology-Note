+ **链接**：[Candy](https://leetcode.com/problems/candy/)

`n`个小孩排成一列分糖果，数组`ratings`记录了每个小孩的分数，所有小孩都至少能得到一个糖果，如果一个小孩比他旁边的小孩高分，他就要得到比旁边的孩子更多的糖果。

求最少需要多少个糖果。

---
## 来回遍历法

+ **复杂度**：$O(n)$ / $O(n)$

这种解法的思想来源于贪心算法。

用一个数组记录每一个小孩分配到的糖果数量，首先每一个孩子先分配一个糖果，然后对数组进行两次遍历：

+ 第一次从左往右遍历，如果有孩子的评分比他左边的孩子高，就让他比左边的孩子多得一个糖果，由此确保每一位孩子得到的糖果数满足左约束。
+ 第二次从右往左遍历，如果有孩子的评分比他右边的孩子高但糖果数比右边的孩子少，就让他比右边的孩子多得一个糖果，由此确保每一位孩子得到的糖果数满足右约束。

最终把所有孩子的糖果数加到一起。

---
## 最优解法

+ **复杂度**：$O(n)$ / $O(1)$

