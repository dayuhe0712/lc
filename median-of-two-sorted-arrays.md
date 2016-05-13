[Link](http://www.jiuzhang.com/solutions/median-of-two-sorted-arrays/)

```java
// 找第K个数，每次消掉K/2个数;
// 在AB中分别找第K/2数，注意当A或B里面不够K/2数的情况（consider tail of A or B as Integer.MAX_VALUE）;
// 结束条件：1. startA(or B) >= A(or B).length 2. K = 1;
public class Solution {
    public double findMedianSortedArrays(int[] A, int[] B) {
        int len = A.length + B.length;
        if (len % 2 == 0) {
            return findKth(A, B, len / 2 + 1);
        } else {
            return (findKth(A, B, len / 2) + findKth(A, B, len / 2 + 1)) / 2.0;
        }
    }
    
     public int findKth(int[] A, int B[], int A_start, int B_start, int k) {
        if (A_start >= A.length) {
            return B[B_start + k - 1];
        }   
        if (B_start >= B.length) {
            return A[A_start + k - 1];
        }
        
        int A_key = A_start + k / 2 - 1 < A.length? A[A_start + k / 2 - 1] : Integer.MAX_VALUE;
        int B_key = B_start + k / 2 - 1 < B.length? B[B_start + k / 2 - 1] : Integer.MAX_VALUE;
        
        
        if (A_key > B_key) {
            return findKth(A, B, A_start + k / 2, B_start, k - k / 2);
        } else {
            return findKth(A, B, A_start, B_start + k / 2, k - k / 2);
        }
    }
}
