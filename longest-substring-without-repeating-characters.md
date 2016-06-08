[Link](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

```java
public class Solution {
    public int lengthOfLongestSubstring(String s) {
        if (s == null) {
            return 0;
        }
	    char[] arr = s.toCharArray();
	    int len = 0;
 
	    HashMap<Character, Integer> map = new HashMap<Character, Integer>();
 
	    for (int i = 0; i < arr.length; i++) {
		    if (!map.containsKey(arr[i])) {
			    map.put(arr[i], i);
		    } else {
			    len = Math.max(len, map.size()); //更新当前最大长度
			    i = map.get(arr[i]); //找当前substring中重复的那个char的下一个位置
			    map.clear(); //重新开始
		    }
	    }
 
	    return Math.max(pre, map.size());
    }
}
