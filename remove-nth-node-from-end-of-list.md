[Link](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        if (head == null)
            return null;
        
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode fast = dummy;
        ListNode slow = dummy;
        
        //fast先跳到第N+1个点
        for (int i = 0; i <= n; i++) {
            fast = fast.next;
        }
        
        //再同时跳
        while (fast != null) {
            fast = fast.next;
            slow = slow.next;
        }
        
        //此时，slow.next即为倒数第n个点
        slow.next = slow.next.next;
        return dummy.next;
    }
}
