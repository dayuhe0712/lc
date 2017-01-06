[Link](https://leetcode.com/problems/copy-list-with-random-pointer/)

```java
/**
 * Definition for singly-linked list with a random pointer.
 * class RandomListNode {
 *     int label;
 *     RandomListNode next, random;
 *     RandomListNode(int x) { this.label = x; }
 * };
 */
public class Solution {
    public RandomListNode copyRandomList(RandomListNode head) {
        if (head == null) {
            return null;
        }
        
        RandomListNode dummy = new RandomListNode(-1);
        dummy.next = head;
        
        //copy next 1-2-3 ---> 1-1'-2-2'-3-3'
        while (head != null) {
            RandomListNode temp = head.next;
            head.next = new RandomListNode(head.label);
            head.next.next = temp;
            head = temp;
        }
        head = dummy.next; //reposition head
        
        //copy random pointer
        while (head != null) {
            if (head.random != null) {
                head.next.random = head.random.next;
            } else {
                head.next.random = null;
            }
            head = head.next.next;
        }
        head = dummy.next; //reposition head again
        
        //split list
        RandomListNode dummy2 = new RandomListNode(-1);
        RandomListNode temp2 = dummy2;
        while (head != null) {
            temp2.next = head.next;
            head = head.next.next; //return original list
            head = head.next;
            temp2 = temp2.next;
        }
        return dummy2.next;
    }
}
