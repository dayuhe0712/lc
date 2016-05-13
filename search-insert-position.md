[Link](https://leetcode.com/problems/search-insert-position/)

```java
//注意返回条件
public class Solution {
    public int searchInsert(int[] nums, int target) {
        if(nums==null || nums.length==0)
            return 0;
        
        int start = 0;
        int end = nums.length - 1;
        
        while(start + 1 < end) {
            int mid = start + (end - start) / 2;
            if (nums[mid] == target) {
                return mid;
            }
            
            if (nums[mid] < target) {
                start = mid;
            } else {
                end = mid;
            }
        }
        
        if (nums[start] >= target) {
            return start;
        } else if (nums[end] >= target) {
            return end;
        } else {
            return end + 1;
        }
    }
}
