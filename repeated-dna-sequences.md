[Link](https://leetcode.com/problems/repeated-dna-sequences/)

```java
public class Solution {
    public List<String> findRepeatedDnaSequences(String s) {
        HashMap<String, Integer> map = new HashMap<String, Integer>();
        for (int i = 0; i <= s.length() - 10; i++) {
            String token = s.substring(i, i + 10);
            if (!map.containsKey(token)) {
                map.put(token, 1);
            } else {
                map.put(token, map.get(token) + 1);
            }
        }
        List<String> res = new ArrayList<String>();
        for (String token : map.keySet()) {
            if (map.get(token) > 1) {
                res.add(token);
            }
        }
        return res;
    }
}
