### Intuition
Inorder traversal of a binary tree involves visiting the left subtree, then the root node, and finally the right subtree. This can be efficiently implemented using a recursive helper function.

### Approach
1. **Recursive Traversal:**
   - Use a helper function to recursively visit nodes.
   - First, recursively traverse the left subtree.
   - Then, visit the root node and add its value to the result list.
   - Finally, recursively traverse the right subtree.

2. **Edge Case:**
   - If the tree is empty (i.e., the root is `null`), return an empty list.

### Complexity
- **Time Complexity:** \(O(n)\), where \(n\) is the number of nodes in the tree. Each node is visited exactly once.
- **Space Complexity:** \(O(n)\), due to the recursive call stack in the worst case (in case of a skewed tree).

### Code
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
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> in = new LinkedList<>();
        helper(root, in);
        return in;
    }

    private void helper(TreeNode root, List<Integer> in) {
        if (root == null) return;

        helper(root.left, in);
        in.add(root.val);
        helper(root.right, in);
    }
}
```

### Explanation
1. **`inorderTraversal` Method:**
   - Initializes an empty list `in` to store the traversal result.
   - Calls the helper function to populate the list.

2. **`helper` Method:**
   - Recursively traverses the left subtree.
   - Adds the root node's value to the list.
   - Recursively traverses the right subtree.

This implementation ensures that we correctly perform the inorder traversal of the binary tree and capture the result in the list `in`.