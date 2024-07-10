Let's break down the problem of finding the middle node in a singly-linked list and analyze the provided solution.

## Intuition
To find the middle node of a singly-linked list, we can use two main approaches:
1. **Two-pass approach**: Count the total number of nodes in the list, then iterate again to the middle node.
2. **One-pass approach**: Use two pointers, where one pointer moves twice as fast as the other. When the faster pointer reaches the end, the slower pointer will be at the middle.

The given solution uses the two-pass approach.

## Approach
1. **Count the Nodes**: Iterate through the linked list to count the total number of nodes.
2. **Find the Middle**: Calculate the index of the middle node (using integer division by 2). Iterate through the list again to this middle index.
3. **Return the Middle Node**: Return the node at the middle index.

## Complexity

### Time Complexity
- The first pass through the linked list to count the nodes takes \(O(n)\).
- The second pass to reach the middle node also takes \(O(n)\).
Therefore, the total time complexity is:
$$O(n)$$

### Space Complexity
- The solution uses a constant amount of extra space for variables such as `count`, `mid`, and pointers `dummy` and `ans`.
Therefore, the space complexity is:
$$O(1)$$

## Code
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode middleNode(ListNode head) {
        if (head == null || head.next == null) {
            return head;
        }

        // Step 1: Count the total number of nodes
        ListNode dummy = head;
        int count = 0;
        while (dummy != null) {
            count++;
            dummy = dummy.next;
        }

        // Step 2: Find the middle index
        int mid = count / 2;

        // Step 3: Iterate to the middle node
        ListNode ans = head;
        int i = 0;
        while (i != mid) {
            ans = ans.next;
            i++;
        }

        // Step 4: Return the middle node
        return ans;
    }
}
```

