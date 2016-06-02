[Link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

```java
public class Solution {
    public int maxProfit(int[] prices) {
        if (prices.length < 2) {
            return 0;
        }
        int len = prices.length;
        int max = 0; //max profit by selling at day[i]
        int currMin = prices[0]; //min price from beginning to current
        for (int i = 1; i < len; i++) {
            currMin = Math.min(currMin, prices[i]);
            max = Math.max(max, prices[i] - currMin);
        }
        return max;
    }
}
