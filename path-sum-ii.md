[Link](https://leetcode.com/problems/path-sum-ii/)

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
    public List<List<Integer>> pathSum(TreeNode root, int sum) {
        List<List<Integer>> rst = new ArrayList<List<Integer>>();
        ArrayList<Integer> solution = new ArrayList<Integer>();

        findSum(rst, solution, root, sum);
        return rst;
    }

    public void findSum(List<List<Integer>> result, ArrayList<Integer> solution, TreeNode root, int sum){
        if (root == null) {
            return;
        }

        sum -= root.val;

        if (root.left == null && root.right == null) {
            if (sum == 0){
                solution.add(root.val);
                result.add(new ArrayList<Integer>(solution));
                solution.remove(solution.size()-1);
            }
            return;
        }

        solution.add(root.val);
        findSum(result, solution, root.left, sum);
        findSum(result, solution, root.right, sum);
        solution.remove(solution.size()-1);
    }
}
