[Link](https://leetcode.com/problems/find-the-duplicate-number/)

```java
//O(nlog(n)), 对可能的结果[1，n]进行二分查找，每次都遍历一遍整个数组。
//注意边界条件！
public class Solution {
    public int findDuplicate(int[] nums) {
        int start = 1;
        int end = nums.length - 1;
        while (start + 1 < end) {
            int val = start + (end - start) / 2;
            int count = countLess(nums, val);
            if (count < val) {
                start = val;
            } else {
                end = val;
            }
        }
        if (countLess(nums, end) < end) {
            return end;
        } else {
            return start;
        }
    }
    
    private int countLess(int[] nums, int val) {
        int number = 0;
        for (int num : nums) {
            if (num < val) {
                number++;
            }
        }
        return number;
    }
}
