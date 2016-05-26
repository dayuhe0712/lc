[Link](https://leetcode.com/problems/wildcard-matching/)

```java
public class Solution {
    public boolean isMatch(String s, String p) {
        if (s == null || p == null) {
            return false;
        }
        
        int m = s.length() + 1;
        int n = p.length() + 1;
        boolean[][] match = new boolean[m][n];
        
        //initial
        match[0][0] = true;
        //s is empty string
        for (int j = 1; j < n; j++) {
            match[0][j] = p.charAt(j - 1) == '*' && match[0][j - 1];
        }
        
        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                if (s.charAt(i - 1) == p.charAt(j - 1) || p.charAt(j - 1) == '?') {
                    match[i][j] = match[i - 1][j - 1];
                } else if (p.charAt(j - 1) == '*') {
                    match[i][j] = match[i - 1][j] || match[i][j - 1];
                }
            }
        }
        
        return match[m - 1][n - 1];
    }
}
