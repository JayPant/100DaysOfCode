### Intuition
To view the right side of a binary tree, we want to capture the last node seen at each level when the tree is traversed level by level. The rightmost node at each level will be visible from the right side.

### Approach
1. **Level Order Traversal:**
   - We use a queue to perform a level order traversal (BFS) of the tree.
   - For each level, we keep track of the last node's value encountered.
   - At the end of each level, this last node value is added to the result list, representing the visible node from the right side for that level.

2. **Queue Management:**
   - We use a `null` marker to denote the end of a level.
   - When encountering a `null` marker, we know we've reached the end of the current level, so we add the last seen node value to the result list and enqueue another `null` if the queue is not empty, marking the end of the next level.

3. **Edge Case:**
   - If the tree is empty (i.e., the root is `null`), we immediately return an empty list.

### Complexity
- **Time Complexity:** \(O(n)\), where \(n\) is the number of nodes in the tree. We visit each node once.
- **Space Complexity:** \(O(n)\), due to the space required to store the nodes in the queue.

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
    public List<Integer> rightSideView(TreeNode root) {
        List<Integer> list = new LinkedList<>();
        if (root == null) {
            return list;
        }

        Queue<TreeNode> q = new LinkedList<>();
        q.add(root);
        q.add(null);
        int prev = -1;
        while (!q.isEmpty()) {
            TreeNode curr = q.remove();
            if (curr == null) {
                if (q.isEmpty()) {
                    list.add(prev);
                    break;
                } else {
                    q.add(null);
                    list.add(prev);
                }
            } else {
                prev = curr.val;
                if (curr.left != null)
                    q.add(curr.left);
                if (curr.right != null)
                    q.add(curr.right);
            }
        }
        return list;
    }
}
```

### Explanation
1. **Initialization:**
   - A list `list` is used to store the result.
   - A queue `q` is used for level order traversal, with the `root` node and a `null` marker initially enqueued.

2. **Processing Each Level:**
   - For each node removed from the queue, we check if it is `null`.
   - If it is `null`, the previous level has ended, so the last non-null node's value (`prev`) is added to `list`, and a new `null` is enqueued if there are more nodes to process.
   - If it is not `null`, we update `prev` with the current node's value and enqueue its left and right children if they exist.

3. **Termination:**
   - The loop continues until the queue is empty, ensuring that all levels are processed. The final `list` contains the right side view of the binary tree.