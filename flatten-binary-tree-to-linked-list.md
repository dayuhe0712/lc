[Link](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/)

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
    TreeNode lastnode = null; //利用一个全局变量，每次把lastnode.left设为null
    public void flatten(TreeNode root) {
        if (root == null) {
            return;
        }
        
        if (lastnode != null) {
            lastnode.left = null;
            lastnode.right = root;
        }
        
        TreeNode right = root.right;
        lastnode = root;
        flatten(root.left);
        flatten(right);
    }
}
