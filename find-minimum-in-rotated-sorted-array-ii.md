[Link](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/)

```java
//与之前的区别：
//跟start比的时候，如果相等，start就往后挪一位
//同理end要往前挪一位

public class Solution {
    public int findMin(int[] nums) {
        if (nums == null || nums.length == 0) {
            return -1;
        }
        
        int start = 0;
        int end = nums.length - 1;
        
        while(start + 1 < end) {
            int mid = start + (end - start) / 2;
            
            if (nums[mid] == nums[end]) {
                end--;
                continue;
            } 
            if (nums[mid] == nums[start]) {
                start++;
                continue;
            }
            
            if (nums[mid] < nums[end]) {
                end = mid;
            } else {
                start = mid;
            }
        }
        
        return Math.min(nums[start], nums[end]);
    }
}
