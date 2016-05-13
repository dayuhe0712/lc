[Link](https://leetcode.com/problems/search-in-rotated-sorted-array/)

```java
public class Solution {
    public int search(int[] nums, int target) {
        if (nums==null || nums.length==0) {
            return -1;
        }
        
        int start = 0;
        int end = nums.length() - 1;
        int mid = start + (end - start) / 2;
        
        while (start + 1 < end) {
            
        }
       
    }
}
