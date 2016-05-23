[Link](https://leetcode.com/problems/reorder-list/)

```java//把list切成2部分，翻转后面的，再合并

/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    private ListNode reverse(ListNode head) {
        ListNode newhead = null;
        while (head != null) {
            ListNode temp = head.next;
            head.next = newhead;
            newhead = head;
            head = head.next;
        }
        return newhead;
    }
    
    private void merge(ListNode head1, ListNode head2) {
        ListNode dummy = new ListNode(0);
        while (head1 != null && head2 != null) {
            dummy.next = head1;
            head1 = head1.next;
            dummy = dummy.next;
            
            dummy.next = head2;
            head2 = head2.next;
            dummy = dummy.next;
        }
        if (head1 != null) {
            dummy.next = head1;
        } else {
            dummy.next = head2;
        }
    }
    
    public void reorderList(ListNode head) {
        if (head == null || head.next == null) {
            return;
        }
        
        //find mid
        ListNode slow = head, fast = head;
        while (fast != null && fast.next != null) {
            slow = head.next;
            fast = head.next.next;
        }
        ListNode head2 = slow.next;
        slow.next = null;
        
        //reverse second half
        ListNode reverse = reverse(head2);
        
        //merge
        merge(head, head2);
    }
}
