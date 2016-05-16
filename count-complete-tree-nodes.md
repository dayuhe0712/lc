[Link](https://leetcode.com/problems/count-complete-tree-nodes/)

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
    public int countNodes(TreeNode root) {

        //count left subtree height
        TreeNode lr = root;
        int leftcount = 0;
        while (lr != null) {
            leftcount++;
            lr = lr.left;
        }
        
        //count right subtree height
        TreeNode rr = root;
        int rightcount = 0;
        while (rr != null) {
            rightcount++;
            rr = rr.right;
        }
        
        if (leftcount == rightcount) {
            return (1 << leftcount) - 1;
        } else {
            return countNodes(root.left) + countNodes(root.right) + 1;
        }
    }
}
