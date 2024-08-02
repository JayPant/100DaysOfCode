## Intuition
The problem requires finding the lowest common ancestor (LCA) of two nodes in a binary tree. The LCA is defined as the deepest node that is an ancestor of both given nodes. The first thought is to traverse the tree and identify the point where the paths to the two nodes diverge, which would be their LCA.

## Approach
1. **Base Cases**:
   - If the current node (`root`) is `null`, we return `null` as there is no ancestor.
   - If the current node is either `p` or `q`, then the current node itself could be an ancestor of the other node, so we return `root`.

2. **Recursive Search**:
   - Recursively search for `p` and `q` in the left subtree (`leftLca`) and the right subtree (`rightLca`).

3. **Determine the LCA**:
   - If both `leftLca` and `rightLca` are not `null`, then the current node (`root`) is the LCA because `p` and `q` are found in different subtrees.
   - If only one of `leftLca` or `rightLca` is not `null`, then return the non-null value. This means both `p` and `q` are located in the same subtree where the non-null value is found.

## Complexity
- **Time Complexity**: \(O(n)\)
  - We potentially visit every node in the binary tree once, where `n` is the number of nodes.

- **Space Complexity**: \(O(n)\)
  - The space complexity is mainly due to the recursion stack. In the worst case (unbalanced tree), the recursion stack can go as deep as the number of nodes in the tree. For a balanced tree, it would be \(O(\log n)\).

## Code
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
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if (root == null || root == p || root == q) return root;

        TreeNode leftLca = lowestCommonAncestor(root.left, p, q);
        TreeNode rightLca = lowestCommonAncestor(root.right, p, q);

        if (leftLca == null) return rightLca;
        if (rightLca == null) return leftLca;

        return root;
    }
}
```
