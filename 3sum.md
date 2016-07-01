[Link](https://leetcode.com/problems/3sum/)

```java
public class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> result = new ArrayList<List<Integer>>();
        Arrays.sort(nums);
        for (int i = 0; i < nums.length - 2; i++) {
            if (i > 0 && nums[i] == nums[i - 1]) {
                continue;
            }
            int low = i + 1;
            int hi = nums.length - 1;
            while (low < hi) {
                int sum = nums[i] + nums[low] + nums[hi];
                if (sum == 0) {
                    List<Integer> temp = new ArrayList<Integer>();
                    temp.add(nums[i]);
                    temp.add(nums[low]);
                    temp.add(nums[hi]);
                    result.add(temp);
                    low++;
                    hi--;
                    
                    while (low < hi && nums[low] == nums[low - 1]) {
                        low++;
                    }
                    while (low < hi && nums[hi] == nums[hi + 1]) {
                        hi--;
                    }
                } else if (sum < 0) {
                    low++;
                } else {
                    hi--;
                }
            }
        }
        return result;
    }
}
