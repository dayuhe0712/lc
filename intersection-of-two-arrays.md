[Link](https://leetcode.com/problems/intersection-of-two-arrays/)

```java
public class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        HashSet<Integer> set1 = new HashSet<Integer>();
        for (int i : nums1) {
            set1.add(i);
        }
        
        HashSet<Integer> set2 = new HashSet<Integer>();
        for (int j : nums2) {
            if (set1.contains(j)) {
                if (!set2.contains(j)) {
                    set2.add(j);
                }
            }
        }
        
        int[] result = new int[set2.size()];
        int i = 0;
        for (int j : set2) {
            result[i++] = j;
        }
        return result;
    }
}
