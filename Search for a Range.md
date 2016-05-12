[Link](https://leetcode.com/problems/search-for-a-range/)

```java
public class Solution {
    public int[] searchRange(int[] nums, int target) {
        if (nums==null || nums.length==0)
            return null;
            
        int start, mid, end;
        int[] result = new int[2];
        
//find left boundary
        start = 0;
        end = nums.length -1; 
        mid = start + (end - start) / 2;
        while (start + 1 < end) {
            if (nums[mid] == target) {
                end = mid;
            }
            if (nums[mid] < target) {
                start = mid;
            } else {
                end = mid;
            }
        }
        if (nums[start] == target) {
            result[0] = start;
        }
        if (nums[end] == target) {
            result[0] = end;
        } else {
            result[0] = result[1] = -1;
            return result;
        }
        

//find right boudary
        start = 0;
        end = nums.length -1; 
        mid = start + (end - start) / 2;
        while (start + 1 < end) {
            if (nums[mid] == target) {
                start = mid;
            }
            if (nums[mid] < target) {
                start = mid;
            } else {
                end = mid;
            }
        }
        if (nums[start] == target) {
            result[1] = start;
        }
        if (nums[end] == target) {
            result[1] = end;
        } else {
            result[0] = result[1] = -1;
            return result;
        }
        
        return result;
    }
}
