[Link](https://leetcode.com/problems/odd-even-linked-list/)

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
    public ListNode oddEvenList(ListNode head) {
        if (head == null || head.next == null) {
            return head;
        }
        ListNode oddDummy = new ListNode(0);
        ListNode evenDummy = new ListNode(0);
        ListNode odd = oddDummy;
        ListNode even = evenDummy;
        int index = 1;
        while (head != null) {
            if (index % 2 == 1) {
                odd.next = head;
                head = head.next;
                odd = odd.next;
            } else {
                even.next = head;
                head = head.next;
                even = even.next;
            }
            index++;
        }
        odd.next = evenDummy.next;
        even.next = null;
        return oddDummy.next;
    }
}
