[Link](https://leetcode.com/problems/maximum-product-subarray/)

```java
//维护局部最大跟最小两个值
public class Solution {
    public int maxProduct(int[] nums) {
        int n = nums.length;
        int[] max = new int[n];
        int[] min = new int[n];
        
        max[0] = min[0] = nums[0];
        int maxProduct = nums[0];
        for (int i = 1; i < n; i++) {
            if (nums[i] > 0) { //nums[i]为正数
                max[i] = Math.max(nums[i], max[i - 1] * nums[i]);
                min[i] = Math.min(nums[i], min[i - 1] * nums[i]);
            } else { //nums[i]为负数
                max[i] = Math.max(nums[i], min[i - 1] * nums[i]);
                min[i] = Math.min(nums[i], max[i - 1] * nums[i]);
            }
            maxProduct = Math.max(maxProduct, max[i]); //更新
        }
        
        return maxProduct;
    }
}
