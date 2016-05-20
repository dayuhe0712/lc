[Link](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/)

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Solution {
    ListNode current;
    public TreeNode sortedListToBST(ListNode head) {
        if (head == null) {
            return null;
        }
        
        int size = 0;
        ListNode node = head;
        while (node != null) {
            node = node.next;
            size++;
        }
        
        current = head;
        return helper(size);
    }
    
    private TreeNode helper(int size) {
        if (size <= 0) {
            return null;
        }
        TreeNode left = helper(size / 2);
        TreeNode root = new TreeNode(current.val);
        current = current.next;
        TreeNode right = helper(size - size / 2 - 1);
        
        root.left = left;
        root.right = right;
        return root;
    }
}
