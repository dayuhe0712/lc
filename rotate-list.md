[Link](https://leetcode.com/problems/rotate-list/)

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
    public ListNode rotateRight(ListNode head, int k) {
        if (head == null || head.next == null) {
            return head;
        }
        
        //find length of the list
        int len = 0;
        ListNode count = head;
        while (head != null) {
            len++;
            head = head.next;
        }
        
        //using fast/slow node to find the kth node from the end
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        head = dummy;
        ListNode fast = dummy;
        ListNode slow = dummy;
        k = k % len; //注意 1. k是可以大于总长度的 2. 如果k % len = 0 则不需挪动list
        for (int i = 0; i < k; i++) {
            fast = fast.next;
        }
        while (fast.next != null) {
            fast = fast.next;
            slow = slow.next;
        }
        fast.next = dummy.next;
        dummy.next = slow.next;
        slow.next = null;
        
        return dummy.next;
    }
}
