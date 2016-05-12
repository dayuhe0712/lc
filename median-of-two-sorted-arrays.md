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
}
