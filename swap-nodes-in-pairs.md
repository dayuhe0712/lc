[Link](https://leetcode.com/problems/swap-nodes-in-pairs/)

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
    public ListNode swapPairs(ListNode head) {
        if (head == null || head.next == null)
            return head;
            
        ListNode dummy = new ListNode(0);
        head = dummy;
        
        while (head != null && head.next.next != null) {
            ListNode l1 = head.next;
            ListNode l2 = head.next.next;
            //head->l1->l2->...
            //head->l2->l1->...
            head.next = l2;
            l1.next = l2.next;
            l2.next = l1;
            head = l1;
        }
        
        return dummy.next;
    }
}
