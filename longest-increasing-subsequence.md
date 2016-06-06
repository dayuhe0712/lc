[Link](https://leetcode.com/problems/longest-increasing-subsequence/)

```java
public class Solution {
    public int lengthOfLIS(int[] nums) {
        if (nums == null || nums.length == 0) {
            return 0;
        }
        
        int[] dp = new int[nums.length]; //记录以nums[i]为结尾的LIS长度 
        int len = 0; //max length
        
        for (int i = 0; i < nums.length; i++) {
            dp[i] = 1; //初始化
            for (int j = 0; j < i; j++) {
                if (nums[i] > nums[j]) {
                    dp[i] = dp[i] > dp[j] + 1 ? dp[i] : dp[j] + 1;
                }
            }
            if (dp[i] > len) {
                len = dp[i];
            }
        }
        
        return len;
    }
}
