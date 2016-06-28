[Link](https://leetcode.com/problems/sum-root-to-leaf-numbers/)

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
    int res = 0;
    public int sumNumbers(TreeNode root) {
        if (root == null) {
            return 0;
        }
        helper(root, 0);
        return res;
    }
    
    private void helper(TreeNode root, int val) {
        if (root.left == null && root.right == null) {
            res += val * 10 + root.val;
        } 
        if (root.left != null) {
            helper(root.left, val * 10 + root.val);
        }
        if (root.right != null) {
            helper(root.right, val * 10 + root.val);
        }
    }
}
