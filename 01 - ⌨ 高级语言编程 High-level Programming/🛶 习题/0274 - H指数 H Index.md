+ **链接**：[H Index](https://leetcode.com/problems/h-index/description/?envType=study-plan-v2&envId=top-interview-150)

计算科研人员的H Index，即最多有`h`篇论文的被引用数不低于`h`

---
## 计数法

+ **复杂度**：时间 $O(n)$ / 空间 $O(n)$

由于H指数不可能超过发表的总论文数`n`，可以用一个数组`cite_cnt`记录从`0`到`n`每一个引用数的论文数数量（引用数超过`n`的论文计入`n`）；从`cite_cnt`的结尾往前遍历，累加统计引用数大于当前引用数`i`的论文数量并与`i`进行比较，当累计的论文数量超过引用数`i`，则输出`i`为`h`

+ 举例：
	+ 论文引用数`[4, 0, 3, 15, 4, 1, 2]`
	+ 对应的`cite_cnt`为`[1, 1, 1, 1, 2, 0, 0, 1]`
		+ $Q_\mathrm{{cite}\geq7}=1<7$
		+ $Q_\mathrm{{cite}\geq6}=1<6$
		+ $Q_\mathrm{{cite}\geq5}=1<5$
		+ $Q_\mathrm{{cite}\geq4}=3<4$
		+ $Q_\mathrm{{cite}\geq3}=4>3$
	+ 则H指数为`3`


---
## 倒序法（最优解法）

+ **复杂度**：时间 $O(n\log n)$ / 空间 $O(1)$

将论文按引用数降序排列，从数学上可以表示为一个优化问题
$$\max\{\min_i [Q_\mathrm{cite,i}, Q_\mathrm{(Q_\mathrm{cite}>Q_\mathrm{cite,i})}]\}$$

