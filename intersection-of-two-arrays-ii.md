[Link](https://leetcode.com/problems/intersection-of-two-arrays-ii/)

```java
public class Solution {
    public int[] intersect(int[] nums1, int[] nums2) {
        HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
        for (int i : nums1) {
            if (map.containsKey(i)) {
                map.put(i, map.get(i) + 1);
            } else {
                map.put(i, 1);
            }
        }
        
        List<Integer> list = new ArrayList<Integer>();
        for (int j : nums2) {
            if (map.containsKey(j)) {
                if (map.get(j) > 1) {
                    map.put(j, map.get(j) - 1);
                } else {
                    map.remove(j);
                }
                list.add(j);
            }
        }
        
        int[] result = new int[list.size()];
        int i = 0;
        for (int j : list) {
            result[i++] = j;
        }
        return result;
    }
}
