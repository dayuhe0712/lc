[Link](https://leetcode.com/problems/recover-binary-search-tree/)

```java
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
    TreeNode first = null;
    TreeNode second = null;
    TreeNode pre = null;
    
    public void recoverTree(TreeNode root) {
        inOrder(root);
        
        int temp = first.val;
        first.val = second.val;
        second.val = temp;
    }
    
    public void inOrder(TreeNode root) {
        if (root == null) {
            return;
        }
        
        inOrder(root.left);
        
        if (pre != null && pre.val > root.val) {
            if (first == null) {
                first = pre;
                second = root;
            } else {
                second = root;
            }
        }
        
        pre = root;
        
        inOrder(root.right);
    }
}
