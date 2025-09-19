+ **链接**：[Gas Station](https://leetcode.com/problems/gas-station/)

环形路径上一共有`i`个加油站，两个`i`维数组分别记录了每个加油站的储油量和顺时针前往下一个加油站路上的耗油量。小车在油箱初始为空的情况下，以某个加油站为起点，绕行环形路径一圈。

判断是否存在一个起点使得小车可以走完全程，如有，返回加油站编号

---
## 回退法

+ 复杂度：时间$O(n)$、空间$O(1)$

回退法的核心思想是，先选择随机一个加油站作为起点，往前开车，当遇到油量不足的路段时将出发点前移，用多出来的汽油补充油箱继续开车。直到出发点和车辆所在位置重合，便找到了可以让小车绕行一圈的出发加油站。

在使用回退法之前，需要判断是否存在可行解。由于小车的汽油可以累积，一个直观的结论是，如果所有加油站的油量之和大于所有路段的耗油之和，则一定存在一个起点使得小车可以走完全程。

```C++
class Solution {
private:
    int size = 0;
    int circularShift(int num) {
        if (num == size) return 0;
        else if (num == -1) return size - 1;
        else return num;
    }
public:
    int canCompleteCircuit(vector<int>& gas, vector<int>& cost) {
        size = gas.size();
        int total = 0;
        for (int i = 0; i < gas.size(); i++) total += (gas[i] - cost[i]);
        if (total < 0) return -1;

        int start = 0, pass = 0;
        int current_gas = gas[0] - cost[0];
        while (true) {
            if (current_gas < 0) {
                start = circularShift(--start);
                current_gas += (gas[start] - cost[start]);
            }
            else {
                pass = circularShift(++pass);
                current_gas += (gas[pass] - cost[pass]);
            }
            if (pass == start) return start;
        }
    }
};
```