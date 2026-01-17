+ **链接**：[Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/?envType=study-plan-v2&envId=top-interview-150)

给定一个记录股价的数组，每天可以买入或卖出，手上只能持有一股，求最大收益

---
## 极值检测法

根据一元函数的特性，只需要确保在价格的极小值点买入，极大值点卖出，就一定能得到价格的最大值。极大值处价格函数趋势由增变为减，应当卖出；极小值处价格趋势由减变为增，应当买入。除此之外，考虑到价格可能不变，需要记录目前为止**最新的价格增减趋势**以更精确地定位最值点。

需要考虑的边缘条件有两个，是否在第一日买入，是否在最后一日卖出。

+ 如果从左到右第一个最值是最大值，第一日要买入
+ 如果从左到右最后一个最值是最小值，最后一天要卖出

```C++
class Solution {
public:
    int maxProfit(vector<int>& prices) {

        int buy_price = 0; // 0(not holding)
        int profit = 0;
        int trend = 0; // 1(rising), -1(falling), 0(unknown)

        for (int i = 0; i < prices.size(); i++) {
            // Check whether to sell at the last date
            if (i == prices.size() - 1) {
                if (trend == 1) profit += (prices[i] - buy_price);
                break;
            }
            
            // Rising
            if (prices[i] < prices[i+1]) {
                // Minimum
                if (trend == -1) buy_price = prices[i];  // Buy if the price begins to rise
                // Buy at start
                if (trend == 0) buy_price = prices[0]; 
                
                trend = 1;
            }

            // Falling
            if (prices[i] > prices[i+1]) {
                // Maximum
                if (trend == 1) {
                    profit += (prices[i] - buy_price);
                    buy_price = 0;
                }
                trend = -1;
            }

        }

        return profit;
    }
};
```