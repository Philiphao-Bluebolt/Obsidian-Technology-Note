+ 链接：[LeetCode](https://leetcode.com/problems/longest-palindromic-substring/description/) | [Wikipedia](https://en.wikipedia.org/wiki/Longest_palindromic_substring)

最长回文子串问题是一个经典的编程问题，始于上世纪六七十年代

---
## Manacher算法

+ **时间复杂度** - $O(n)$

基本思想是利用回文子串的对称性将检测范围减半

---
## 我的解法（中心延伸法的变体）

+ **时间复杂度** - $O(n^2)$

基本思想是使用两层迭代，第一层迭代选择回文子串的中心字符（偶数子串则是中间靠左的字符），第二层迭代从中心字符向两边延申，找到以这个字符为中心的最长回文子串。

实现的优化：

+ 如果靠后的字符作为回文中心时无法得到比已有更长的子串，直接跳过（比如最长是5，倒数第3个字符开始不可能出现长于5的回文串）
+ 第二层迭代使用之字形延申，交替检查奇数和偶数仍否回文串，减少遍历次数（实际上是无效优化，甚至把逻辑弄得更复杂）

```java
class Solution {  
    public String longestPalindrome(String s) {  
        int longest = 0;  
        String result = "";  
  
        // Testing index shift  
        int right = 0;  
        int left = 0;  
        int checking_cnt = 1;  
  
        // In a row of testing, mark if odd or even sequence reach end  
        boolean odd_end = false;  
        boolean even_end = false;  
  
        // Skip some center-index i with no possibility to get a longer string at the end  
        int skip = 0;  
  
        for (int i = 0; i < s.length() - skip; i++)  
        {  
            // Test the palindromic centered at i  
            while(true)  
            {  
                // Testing index out of bound  
                if (i + right >= s.length() || i - left < 0)  
                {  
                    if (checking_cnt % 2 == 1)  
                    {  
                        left--;  
                        if (even_end == true) right--;  
                    }  
                    else  
                    {  
                        right--;  
                        if (odd_end == true) left--;  
                    }  
                    break;  
                }  
  
                System.out.printf("Substring: %s, i = %d, left = %d, right = %d\n", s.substring(i - left, i + right + 1), i, left, right);  
  
                // end of palindromic sequence  
                if (s.charAt(i + right) != s.charAt(i - left))  
                {  
                    if (checking_cnt % 2 == 1) odd_end = true;  
                    else even_end = true;  
  
                    if (odd_end && even_end == true)  
                    {  
                        right--;  
                        left--;  
                        break;  
                    }  
                }  
  
                if (checking_cnt % 2 == 1) right++; // Odd  
                else left++; // Even  
                checking_cnt++;  
            }  
  
            // compare the test result with the previous longest  
            if (left + right + 1 > longest)  
            {  
                System.out.printf("Result Substring: %s, i = %d, left = %d, right = %d\n", s.substring(i - left, i + right + 1), i, left, right); 
                 
                longest = left + right + 1;  
                result = s.substring(i - left, i + right + 1);  
  
                // skip  
                if (longest % 2 == 1) skip = (longest + 1) / 2;  
                else skip = longest / 2;  
            }  
  
            right = 0;  
            left = 0;  
            odd_end = false;  
            even_end = false;  
            checking_cnt = 1;  
        }  
  
        return result;  
    }  
}
```


