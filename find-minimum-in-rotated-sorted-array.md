[Link](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

```java
//注意：每次比较的都是同一个值 nums[nums.length - 1], 而不是可能会更新的nums[end].
public class Solution {
    public int findMin(int[] nums) {
        if (nums == null || nums.length == 0) {
            return -1;
        }
        
        int start = 0;
        int end = nums.length - 1;
        int target = nums[nums.length - 1];
        
        
        while(start + 1 < end) {
            int mid = start + (end - start) / 2;
            if (nums[mid] <= target) {
                end = mid;
            } else {
                start = mid;
            }
        }
        
        if (nums[start] < nums[end]) {
            return nums[start];
        } else {
            return nums[end];
        }
    }
}
