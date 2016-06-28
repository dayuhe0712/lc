[Link](https://leetcode.com/problems/binary-tree-preorder-traversal/)

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
    
    List<Integer> res = new ArrayList<Integer>();
    
    public List<Integer> preorderTraversal(TreeNode root) {
        if (root != null) {
            helper(root);
        }
        return res;
    }
    
    public void helper(TreeNode p) {
        res.add(p.val);
        
        if (p.left != null) {
            helper(p.left);
        }
        
        if (p.right != null) {
            helper(p.right);
        }
    }
}
