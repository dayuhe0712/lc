[Link](https://leetcode.com/problems/h-index/)

```java
public class Solution {
    public int hIndex(int[] citations) {
        // 排序
        Arrays.sort(citations);
        int h = 0;
        for(int i = 0; i < citations.length; i++){
            // 得到当前的H指数
            int currH = Math.min(citations[i], citations.length - i);
            if(currH > h){
                h = currH;
            }
        }
        return h;
    }
}
