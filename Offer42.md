# 剑指 Offer 42. 连续子数组的最大和

## 题目要求
输入一个整型数组，数组中的一个或连续多个整数组成一个子数组。求所有子数组的和的最大值。
要求时间复杂度为`O(n)`。
## C++代码 I
```C
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        vector<int>dp(nums.size(),0);
        dp[0] = nums[0];
        int res = dp[0];
        for(int i=1;i<nums.size();i++){
            dp[i] = max(dp[i-1]+nums[i],nums[i]);
            res = max(res,dp[i]);
        }
            return res;
    }
};
```
## C++代码 II 优化内存
```C
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int dp0 = nums[0];
        int dp1 = dp0;
        int res = dp0;
        for(int i=1;i<nums.size();i++){
            dp1 = max(dp0+nums[i],nums[i]);
            res = max(res,dp1);
            dp0 = dp1;
        }
            return res;
    }
};
```
