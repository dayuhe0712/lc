[Link](https://leetcode.com/problems/add-two-numbers/)

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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        int carry = 0;
        ListNode dummy = new ListNode(0);
        ListNode node = dummy;
        
        while (l1 != null && l2 != null) {
            int sum = carry + l1.val + l2.val;
            node.next = new ListNode(sum % 10);
            carry = sum / 10;
            l1 = l1.next;
            l2 = l2.next;
            node = node.next;
        }
        
        while (l1 != null) {
            int sum = carry + l1.val;
            node.next = new ListNode(sum % 10);
            carry = sum / 10;
            l1 = l1.next;
            node = node.next;
        }
        
        while (l2 != null) {
            int sum = carry + l2.val;
            node.next = new ListNode(sum % 10);
            carry = sum / 10;
            l2 = l2.next;
            node = node.next;
        }
        
        if (carry == 1) {
            node.next = new ListNode(1);
        } 
        
        return dummy.next;
    }
}
