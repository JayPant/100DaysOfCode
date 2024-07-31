## Intuition
The problem asks if a given tree `subRoot` is a subtree of another tree `root`. A tree `subRoot` is a subtree of `root` if there exists a node in `root` such that the subtree rooted at that node is identical to `subRoot`. To solve this problem, we need to traverse the `root` tree and, for each node, check if the subtree rooted at that node is identical to `subRoot`.

## Approach
1. **Recursive Check for Identical Trees**: 
   - Implement a helper function `isIdentical` that checks if two trees are identical. Two trees are identical if:
     - They are both `null` (base case).
     - They have the same root value.
     - Their left subtrees are identical, and their right subtrees are identical.

2. **Recursive Subtree Search**:
   - Implement the main function `isSubtree` to check if `subRoot` is a subtree of `root`. For each node in `root`, it checks:
     - If `root` is `null`, `subRoot` can't be a subtree, so return `false`.
     - If the current node's value matches `subRoot`'s value, check if the trees rooted at these nodes are identical using `isIdentical`.
     - Recursively check if `subRoot` is a subtree of the left subtree of `root` or the right subtree of `root`.

3. **Edge Case**:
   - If `root` is `null`, return `false` as an empty tree cannot contain a non-empty subtree.

## Complexity
- **Time Complexity**: \(O(n \times m)\)
  - `n` is the number of nodes in `root`, and `m` is the number of nodes in `subRoot`.
  - In the worst case, for each node in `root`, we may need to compare all nodes in `subRoot` to check for identical trees.

- **Space Complexity**: \(O(\text{max}(h1, h2))\)
  - Where `h1` and `h2` are the heights of `root` and `subRoot`, respectively.
  - This accounts for the recursion stack.

## Code
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {

    private boolean isIdentical(TreeNode root, TreeNode subRoot){
        if(root == null && subRoot == null){
            return true;
        }
        if(root == null || subRoot == null || root.val != subRoot.val){
            return false;
        }

        return isIdentical(root.left, subRoot.left) && isIdentical(root.right, subRoot.right);
    }

    public boolean isSubtree(TreeNode root, TreeNode subRoot) {
        if(root == null) {
            return false;
        }

        if(isIdentical(root, subRoot)) {
            return true;
        }

        return isSubtree(root.left, subRoot) || isSubtree(root.right, subRoot);
    }
}
```
