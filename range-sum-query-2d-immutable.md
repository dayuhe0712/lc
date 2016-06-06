[Link](https://leetcode.com/problems/range-sum-query-2d-immutable/)

```java
//3  0  1           0    0    0    0
//5  6  3  ===>>>   0    3    3    4
//1  2  0           0    8   14   18
//                  0    9   17   21


public class NumMatrix {
    private int[][] dp; 
    public NumMatrix(int[][] matrix) {
        if (matrix == null || matrix.length == 0 || matrix[0].length == 0) {
            return;
        }
        
        int m = matrix.length + 1;
        int n = matrix[0].length + 1;
        dp = new int[m][n];
        
        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                dp[i][j] = dp[i - 1][j]
                         + dp[i][j - 1]
                         - dp[i - 1][j - 1]
                         + matrix[i - 1][j - 1];
            }
        }
    }

    public int sumRegion(int row1, int col1, int row2, int col2) {
        return dp[row2 + 1][col2 + 1] 
                - dp[row2 + 1][col1]
                - dp[row1][col2 + 1]
                + dp[row1][col1];
    }
}


// Your NumMatrix object will be instantiated and called as such:
// NumMatrix numMatrix = new NumMatrix(matrix);
// numMatrix.sumRegion(0, 1, 2, 3);
// numMatrix.sumRegion(1, 2, 3, 4);
