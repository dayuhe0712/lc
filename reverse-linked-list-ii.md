[Link](https://leetcode.com/problems/reverse-linked-list-ii/)

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
    public ListNode reverseBetween(ListNode head, int m, int n) {
        if (m >= n || head == null) {
            return head;
        }
        
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        head = dummy;
        
        //find the (m-1)th node 
        for (int i = 1; i < m; i++) {
            if (head.next == null) {
                return null;
            }
            head = head.next;
        }
        
        //1->2->3->4->5->NULL
        //1->4->3->2->5->NULL
        ListNode pre = head;
        ListNode mnode = head.next;
        ListNode nnode = mnode, post = mnode.next;
        //mnode never change in for-loop
        //when loop stops, pre = (m-1)th node, post = (n+1)th node
        for (int i = m; i < n; i++) {
            if (post == null) {
                return null;
            }
            ListNode temp = post.next;
            post.next = nnode;
            nnode = post;
            post = temp;
        }
        mnode.next = post;
        pre.next = nnode;
        
        return dummy.next;
    }
}
