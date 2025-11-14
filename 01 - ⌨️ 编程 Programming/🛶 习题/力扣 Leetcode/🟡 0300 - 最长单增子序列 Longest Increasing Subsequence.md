+ 链接 - [Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/submissions/1828812091/)

给定一个数组，在其中任意删除某些元素后形成的序列称为子序列，求最长的严格单调递增的子序列长度。

---
## 思路

这题看似简单，实际上解法非常精巧，很难一下子就想到最优的解法。

最优解法可行的条件是题目只需要求最长单增子序列的长度而非具体的序列。这种方法的工作原理是，每当遇到一个比出现过的数小的数，单增序列都会分化出另一种可能的组合，如果新分支的单增子序列不比过去的组合长，就不影响最长的长度，否则这个分支会取代旧的组合。

+ 遍历整个数组，把元素存放到另一个数组`seq`中
	+ 若当前元素比上一个元素大，直接后接在`seq`尾部
	+ 若当前元素小于或等于上一个元素，在`seq`内部二分查找，替换掉第一个不小于它的数。

以`[0,1,0,3,2,3]`为例，最长单增子序列长度为4

+ 第一个数`0`直接写入，`seq=[0]`
+ 第二个数`1`比尾数大，直接后接，`seq=[0, 1]`
+ 第三个数`0`比尾数小，查找到`seq`中第一个不小于它的数是`0`，直接替换，`seq=[0, 1]`
+ 第四个数`3`比尾数大，直接后接，`seq=[0, 1, 3]`
+ 第五个数`2`比尾数小，查找到`seq`中第一个不小于它的数是`3`，直接替换，`seq=[0, 1, 2]`
+ 最后一个数`3`比尾数大，直接后接，`seq=[0, 1, 2, 3]`

---
## 代码

+ 复杂度 - $O(n\log(n))$ / $O(n)$


```cpp
class Solution {
private:
    int binarySearch(const vector<int>& arr, int i){
        int low = 0;
        int high = arr.size()-1;
        int mid;
        
        while(low <= high){
            mid = low + (high - low) / 2;
            cout << low << " " << mid << " " << high << "\n";
            if (arr[mid] < i) low = mid + 1;
            else if (mid == 0 || arr[mid-1] >= i) high = mid - 1;
            else break;
        }

        return mid;
    }

public:
    int lengthOfLIS(vector<int>& nums) {
            
        vector<int> seq;
        for (int i : nums){
            if (seq.size() == 0) seq.push_back(nums[0]);
            else if (i > seq[seq.size()-1]) seq.push_back(i);
            else seq[binarySearch(seq, i)] = i;    
        }
        return seq.size();
    }
};
```