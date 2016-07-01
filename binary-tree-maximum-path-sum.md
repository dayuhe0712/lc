[Link](https://leetcode.com/problems/binary-tree-maximum-path-sum/)

``java
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
    public int maxPathSum(TreeNode root) {
        // res[0]: single path, 从root往下走到任意点的最大路径，这条路径可以不包含任何点
        // res[1]: global path, 从树中任意到任意点的最大路径，这条路径至少包含一个点
        int[] res = help(root);
        return res[1];
    }
    private int[] help(TreeNode root) {
        if (root == null) {
            return new int[]{0, Integer.MIN_VALUE};
        }
        
        //Divide
        int[] left = help(root.left);
        int[] right = help(root.right);
        
        //Conquer
        int singlePath = Math.max(0, Math.max(left[0], right[0]) + root.val); 
        int globalPath = Math.max(root.val + left[0] + right[0], Math.max(left[1], right[1]));
        return new int[]{singlePath, globalPath};
    }
}
