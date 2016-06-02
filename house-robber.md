[Link](https://leetcode.com/problems/house-robber/)

```java
public class Solution {
    public int rob(int[] nums) {
        if (nums == null || nums.length == 0) {
            return 0;
        }
        if (nums.length == 1) {
            return nums[0];
        }
        
        int n = nums.length;
        int[] max = new int[n]; 
        max[0] = nums[0];
        max[1] = Math.max(nums[0], nums[1]);
        
        for (int i = 2; i < n; i++) {
            max[i] = Math.max((max[i - 2] + nums[i]), max[i - 1]);
        }
        
        return max[n - 1];
    }
}
