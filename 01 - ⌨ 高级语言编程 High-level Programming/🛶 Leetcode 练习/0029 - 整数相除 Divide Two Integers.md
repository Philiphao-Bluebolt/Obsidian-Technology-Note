+ **链接**：[Divide Two Integers](https://leetcode.com/problems/divide-two-integers/)

不使用原生乘除法和求余运算符，实现两个32位有符号整型数的除法

---
## 长除法

+ **时间复杂度**：$O(1)$（只与整型范围有关）

这个问题实际上可以使用二进制的长除算法（小学的竖式除法）解决。长除法的基本原理是将大数的除法分解为从大到小不同数位的除法，以十进制的整数除法（$81427\div29$）为例

+ 第零步（$8\div29=0\dots8$）本质上是（$81427\div290000=0\dots81427$）
+ 第一步（$81\div29=2\dots23$）本质上是（$81427\div29000=2\dots23427$）
+ 第二步（$234\div29=8\dots2$）本质上是（$23400\div2900=8\dots227$）
+ 第三步（$22\div29=0\dots22$）本质上是（$227\div290=0\dots227$）
+ 第四步（$227\div29=7\dots24$）本质上是（$227\div29=7\dots24$）
+ 最后结果：商为2807，余数为24

观察这个计算过程，可以发现长除法的计算原理实际上是通过移动除数的数位（即除数不断除以10）实现的。这个过程可以总结成这样一个算法：

+ 一开始，除数乘以一个较大的10的幂次方**倍率**，成为一个比被除数还要大的数
+ 然后，除数的数位开始右移（即除以10），直到**倍率**回到1
	+ 每移一位都除一下被除数
	+ 商就是最终商对应**倍率**的数位
	+ 余数作为新的被除数

实际上，长除法适用于所有数位的运算，对二进制数来说：

+ ”除数乘以幂次方倍率“ --> 比特向左移位
+ “除数每移一位除一下被除数” --> 大小比较，除数>被除数商为0，除数<被除数商为1
+ 负数应转换为正数才能参与运算
+ 边界条件
	+ 溢出：被除数为整型最小值，除数为-1

---
## Tips

+ 整型`int`的最大最小值可以用`INT_MAX`、`INT_MIN`表示
+ 比特移位以后别忘了赋值`n = n << 1`
+ `INT_MIN`取相反数会溢出，中间变量可以用`long long`防止溢出

---
## 源码

```C++
class Solution {
public:
    int divide(int dividend, int divisor) {
        // Handling the overflow
        if (dividend == INT_MIN && divisor == -1) return INT_MAX;
        if (divisor == 1) return dividend;

        // cout << INT_MIN << " " << INT_MAX;

        // Convert neg to pos
        int sign = (dividend < 0) ^ (divisor < 0) ? -1 : 1;
        long long n = abs((long long)dividend);
        long long d = abs((long long)divisor);

        // Long division
        int mv_cnt = 0;
        int ans = 0;
        while (n > d) 
        {   
            d = d << 1;
            mv_cnt++;
        }

        // cout << mv_cnt << " " << n << " " << d << "\n";

        while (mv_cnt >= 0)
        {
            if (d <= n) 
            {
                ans += (1 << mv_cnt);
                n -= d;
            }
            // cout << mv_cnt << " " << n << " " << d << "\n";
            d = d >> 1;
            mv_cnt--;
        }

        return sign * ans;
    }
};
```