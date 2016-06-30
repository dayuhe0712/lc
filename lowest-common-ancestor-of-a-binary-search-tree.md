[Link](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)

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
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        while ((p.val - root.val) * (q.val - root.val) > 0) { //both p and q on the same subtree
            if (p.val > root.val) {
                root = root.right; //go right subtree
            } else {
                root = root.left; //go left subtree
            }
        }
        return root;
    }
}
