[Link](https://leetcode.com/problems/merge-k-sorted-lists/)
* 注意PriorityQueue的使用
  * 构造函数第一个参数是size， 不能为0，所以输入参数检查必要
  * 重写Comparator

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    private class MyComparator implements Comparator<ListNode> {
        public int compare(ListNode n1, ListNode n2) {
            return n1.val - n2.val;
        }
    }
    
    public ListNode mergeKLists(ListNode[] lists) {
        if (lists == null || lists.length == 0) {
            return null;
        }
        
        //初始化PriorityQueue
        PriorityQueue<ListNode> queue = new PriorityQueue(lists.length, new MyComparator());
        for (int i = 0; i < lists.length; i++) {
            if (lists[i] != null) {
                queue.offer(lists[i]);
            }
        }
        
        ListNode dummy = new ListNode(0);
        ListNode node = dummy;
        while (!queue.isEmpty()) {
            ListNode temp = queue.poll();
            node.next = temp; 
            node = node.next;
            if (temp.next != null) {
                queue.offer(temp.next);
            }
        }
        
        return dummy.next;
    }
}
