[Link](https://leetcode.com/problems/search-a-2d-matrix/)

```java
public class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        if(matrix==null || matrix.length==0 || matrix[0].length==0)
            return false;
        
        int rows = matrix.length;
        int cols = matrix[0].length;
        
        int start = 0;
        int end = rows * cols - 1;
        
        while (start + 1 < end) {
            int mid = start + (end - start) / 2;
            int midValue = matrix[mid / cols][mid % cols];
            if(midValue == target) 
                return true;
            if(midValue > target) {
                end = mid;
            }
            else {
                start = mid;
            }
        }
        
        if (matrix[start / cols][start % cols] == target) {
            return true;
        } else if (matrix[end / cols][end % cols] == target) {
            return true;
        }
        
        return false;
    }
}
