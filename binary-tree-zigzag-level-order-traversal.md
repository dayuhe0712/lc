[Link](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)

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
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<List<Integer>>();
        if (root == null) {
            return result;
        }
        
        Stack<TreeNode> currLevel = new Stack<TreeNode>();
        Stack<TreeNode> nextLevel = new Stack<TreeNode>();
        currLevel.push(root);
        boolean goRight = true;
        
        while (!currLevel.isEmpty()) {
            List<Integer> level = new ArrayList<Integer>();
            while (!currLevel.isEmpty()) { 
                TreeNode node = currLevel.pop();
                level.add(node.val);
                
                //注意：如果要从右往左的顺序，则push进stack的顺序要正好相反的从左向右
                if (!goRight) {
                    if (node.right != null) {
                        nextLevel.push(node.right);
                    }
                    if (node.left != null) {
                        nextLevel.push(node.left);
                    }
                } else {
                    if (node.left != null) {
                        nextLevel.push(node.left);
                    }
                    if (node.right != null) {
                        nextLevel.push(node.right);
                    }
                }
            }
            goRight = !goRight;
            result.add(level);
            Stack<TreeNode> temp = currLevel; //此时为空
            currLevel = nextLevel; //新的currLevel
            nextLevel = temp; //为空
        }
        return result;
    }
}
