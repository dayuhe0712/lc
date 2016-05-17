[Link](https://leetcode.com/problems/first-bad-version/)

```java
/* The isBadVersion API is defined in the parent class VersionControl.
      boolean isBadVersion(int version); */

public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        int start = 1;
        int end = n;
        while (start + 1 < end) {
            int mid = start + (end - start) / 2;
            if (!isBadVersion(mid)) {
                start = mid;
            } else {
                end = mid;
            }
        }
        if (isBadVersion(start)) {
            return start;
        } else if (isBadVersion(end)) {
            return end;
        } else {
            return -1;
        }
    }
}