### Intuition
Postorder traversal of a binary tree involves visiting the left subtree, then the right subtree, and finally the root node. We can achieve this using a recursive helper function.

### Approach
1. **Recursive Traversal:**
   - Use a helper function to recursively visit nodes.
   - First, recursively traverse the left subtree.
   - Then, recursively traverse the right subtree.
   - Finally, visit the root node and add its value to the result list.

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
    public List<Integer> postorderTraversal(TreeNode root) {
        List<Integer> post = new LinkedList<>();
        helper(root, post);
        return post;
    }

    private void helper(TreeNode root, List<Integer> post) {
        if (root == null) return;

        helper(root.left, post);
        helper(root.right, post);
        post.add(root.val);
    }
}
```

### Explanation
1. **`postorderTraversal` Method:**
   - Initializes an empty list `post` to store the traversal result.
   - Calls the helper function to populate the list.

2. **`helper` Method:**
   - Recursively traverses the left subtree.
   - Recursively traverses the right subtree.
   - Adds the root node's value to the list.

