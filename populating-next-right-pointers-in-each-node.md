[Link](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)

```java
/**
 * Definition for binary tree with next pointer.
 * public class TreeLinkNode {
 *     int val;
 *     TreeLinkNode left, right, next;
 *     TreeLinkNode(int x) { val = x; }
 * }
 */
public class Solution {
    public void connect(TreeLinkNode root) {
        if (root == null) {
            return;
        }
        
        TreeLinkNode nextLevelhead = root;
        while (nextLevelhead != null) {
            TreeLinkNode move = nextLevelhead;
            nextLevelhead = null;
            TreeLinkNode prev = null;
            while (move != null) {
                if (move.left != null) { //full binary tree, don't need && move.right
                    if (nextLevelhead == null) {
                        nextLevelhead = move.left;
                    }
                    if (prev != null) {
                        prev.next = move.left;
                    }
                    move.left.next = move.right;
                    prev = move.right;   //prev 每次都是取父节点的右子节点，然后在next level的时候重新更新为null
                }
                move = move.next; //在同一level中自左向右
            }
        }
    }
}
