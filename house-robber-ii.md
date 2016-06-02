[Link](https://leetcode.com/problems/house-robber-ii/)

```java
//做两次dp，一次不一定不包含第一个(1 to n-1)，一次一定不包含第一个(2 to n)
public class Solution {
    public int rob(int[] nums) {
        if (nums == null || nums.length == 0) {
            return 0;
        }
        if (nums.length == 1) {
            return nums[0];
        }
        
        return Math.max(helper(nums, 0, nums.length - 2), helper(nums, 1, nums.length - 1));
    }
    
    public int helper(int[] nums, int start, int end) {
        if (start == end) {
            return nums[start];
        }
        int[] dp = new int[end - start + 1];
        dp[0] = nums[start];
        dp[1] = Math.max(nums[start + 1], dp[0]);
        for (int i = 2; i < dp.length; i++) {
            dp[i] = Math.max((dp[i - 2] + nums[start + i]), dp[i - 1]);
        }
        return dp[dp.length - 1];
    }
}
