[Link](https://leetcode.com/problems/coin-change/)

```java
public class Solution {
    // dp[x + c] = min(dp[x] + 1, dp[x + c])
    // 其中dp[x]代表凑齐金额x所需的最少硬币数，c为可用的硬币面值
    public int coinChange(int[] coins, int amount) {
        int[] dp = new int[amount + 1];
        Arrays.fill(dp, -1);
        dp[0] = 0;
        for (int x = 0; x < amount; x++) {
            if (dp[x] == -1) {
                continue;
            }
            for (int c : coins) {
                if (x + c > amount) {
                    continue;
                }
                if (dp[x + c] == -1 || dp[x + c] > dp[x] + 1) {
                    dp[x + c] = dp[x] + 1;
                }
            }
        }
        return dp[amount];
    }
}
