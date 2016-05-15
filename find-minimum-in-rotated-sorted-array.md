[Link](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

```java
public class Solution {
    public int findMin(int[] nums) {
        if (nums == null || nums.length == 0) {
            return -1;
        }
        
        int start = 0;
        int end = nums.length - 1;
//        int target = nums[nums.length - 1];
        
        while(start + 1 < end) {
            int mid = start + (end - start) / 2;
            if (nums[mid] <= nums[end]) {
                end = mid;
            } else {
                start = mid;
            }
        }
        
        return Math.min(nums[start], nums[end]);
    }
}
