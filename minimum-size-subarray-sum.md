[Link](https://leetcode.com/problems/minimum-size-subarray-sum/)

```java
//一个滑动窗口，双指针
public class Solution {
    public int minSubArrayLen(int s, int[] nums) {
        if (nums == null || nums.length == 0) {
            return 0;
        }
        int i = 0, j = 0;
        int sum = 0;
        int len = Integer.MAX_VALUE;
        for (i = 0; i < nums.length; i++) {
            while (j < nums.length && sum < s) {
                sum += nums[j];
                j++;
            }
            if (sum >= s) {
                len = Math.min(len, j - i);
            }
            sum -= nums[i];
        }
        if (len == Integer.MAX_VALUE) {
            return 0;
        }
        return len;
    }
}
