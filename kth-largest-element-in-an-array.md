[Link](https://leetcode.com/problems/kth-largest-element-in-an-array/)

```java
public class Solution {
    public int findKthLargest(int[] nums, int k) {
        PriorityQueue<Integer> p = new PriorityQueue<Integer>();
        for(int i = 0 ; i < nums.length; i++){
            p.add(nums[i]);
            if(p.size() > k) p.poll();
        }
        return p.poll();
    }
}
