[Link](https://leetcode.com/problems/happy-number/)

```java
public class Solution {
    public boolean isHappy(int n) {
        HashSet<Integer> set = new HashSet<Integer>();
        while (n != 1) {
            if (set.contains(n)) {
                return false;
            } else {
                set.add(n);
                n = getNext(n);
            }
        }
        return true;
    }
    
    private int getNext(int n) {
        int next = 0;
        while (n != 0) {
            next += (n % 10) * (n % 10);
            n = n / 10;
        }
        return next;
    }
}
