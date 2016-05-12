[Link](https://leetcode.com/problems/search-a-2d-matrix-ii/)

```java
public class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        if (matrix == null) {
            return false;
        }
        
        int m = matrix.length, n = matrix[0].length;
        int row = m - 1, col = 0;
        while (row >= 0 && col < n) {
            if (matrix[row][col] == target) {
                return true;
            } else if (matrix[row][col] > target) {
                row--;
            } else {
                col++;
            }
        }
        return false;
    }
}
