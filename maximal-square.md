[Link](https://leetcode.com/problems/maximal-square/)

```java
//dp[i][j]表示以matrix[i][j]为右下角的正方形的边长

public class Solution {
    public int maximalSquare(char[][] matrix) {
        if (matrix == null || matrix.length == 0 || matrix[0].length == 0) {
            return 0;
        }
        
        int m = matrix.length;
        int n = matrix[0].length;
        int[][] dp = new int[m][n];
        
        //initial
        for (int i = 0; i < m; i++) {
            dp[i][0] = matrix[i][0] == '1' ? 1 : 0;
        }
        for (int j = 0; j < n; j++) {
            dp[0][j] = matrix[0][j] == '1' ? 1 : 0;
        }
        
        //general case
        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                if (matrix[i][j] == '1') {
                    dp[i][j] = Math.min(Math.min(dp[i - 1][j], dp[i][j - 1]), dp[i - 1][j - 1]) + 1;
                } else {
                    dp[i][j] = 0;
                }
            }
        }
        
        //get max
        int max = 0;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (dp[i][j] > max) {
                    max = dp[i][j];
                }
            }
        }
        
        return max * max;
    }
}
