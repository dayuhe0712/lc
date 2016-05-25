[Link](https://leetcode.com/problems/unique-binary-search-trees/)

```java
public class Solution {
    public int numTrees(int n) {
        //f(0) = 1
        //f(n) = f(0)*f(n-1) + f(1)*f(n-2) + ... + f(n-2)*f(1) + f(n-1)*f(0)
        int[] dp = new int[n + 1];
        dp[0] = 1;
        
        for (int i = 1; i < n + 1; i++) {
            for (int j = 0; j < i; j++) {
                dp[i] += dp[j] * dp[i - 1 - j];
            }
        }
        
        return dp[n];
    }
}
