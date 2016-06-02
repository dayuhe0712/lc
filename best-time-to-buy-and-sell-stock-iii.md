[Link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/)

```java
//以i天为界，计算preProfit跟postProfit，加在一起。
public class Solution {
    public int maxProfit(int[] prices) {
        if (prices.length < 2) {
            return 0;
        }
        
        int n = prices.length;
        int[] preProfit = new int[n];
        int[] postProfit = new int[n];
        
        int currMin = prices[0]; //从左往右,保留currMin
        preProfit[0] = 0;
        for (int i = 1; i < n; i++) {
            currMin = Math.min(currMin, prices[i]);
            preProfit[i] = Math.max(preProfit[i - 1], prices[i] - currMin);
        }
        
        int currMax = prices[n - 1]; //从右往左，保留currMax
        postProfit[n - 1] = 0;
        for (int j = n - 2; j >= 0; j--) {
            currMax = Math.max(currMax, prices[j]);
            postProfit[j] = Math.max(postProfit[j + 1], currMax - prices[j]);
        }
        
        int maxProfit = 0;
        for (int i = 0; i < n; i++) {
            maxProfit = Math.max(maxProfit, preProfit[i] + postProfit[i]);
        }
        return maxProfit;
    }
}
