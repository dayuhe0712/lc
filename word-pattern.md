[Link](https://leetcode.com/problems/word-pattern/)

```java
public class Solution {
    public boolean wordPattern(String pattern, String str) {
        String[] strs = str.split(" ");
        if (strs.length != pattern.length()) {
            return false;
        }
        
        HashMap<Character, String> map = new HashMap<Character, String>();
        HashSet<String> set = new HashSet<String>();
        for (int i = 0; i < pattern.length(); i++) {
            char c = pattern.charAt(i);
            String s = strs[i];
            if (map.containsKey(c)) {
                if (!map.get(c).equals(s)) {
                    return false;
                }
            } else {
                if (set.contains(s)) { //abba --- dog dog dog dog情况
                    return false;
                } else {
                    map.put(c, s);
                    set.add(s);
                }
            }
        }
        return true;
    }
}
