
# Intuition
The problem of reversing a linked list involves changing the direction of pointers so that each node points to its previous node instead of the next one. Initially, the head node becomes the last node in the reversed list, and the current node moves forward until the end of the original list.

# Approach
1. **Initialization**: Start with three pointers:
   - `prev` initialized to `null` (because the previous of the head becomes `null` in the reversed list).
   - `curr` initialized to `head`, which starts at the original head of the list.
   - `next`, which will temporarily store the next node of `curr` to avoid losing the reference when modifying pointers.

2. **Iterative Reversal**: Traverse through the linked list with `curr`:
   - Store `curr.next` in `next` to prevent losing the reference to the next node.
   - Reverse the `curr` node's pointer to point backwards to `prev` (`curr.next = prev`).
   - Move `prev` and `curr` one step forward: `prev` becomes `curr`, and `curr` becomes `next`.

3. **Completion**: Once `curr` is `null`, `prev` will be pointing to the new head of the reversed list.

4. **Return**: Return `prev`, which is now the head of the reversed list.

# Complexity
- **Time complexity**: \( O(n) \), where \( n \) is the number of nodes in the linked list. This is because we traverse the list once.
- **Space complexity**: \( O(1) \). We use only a constant amount of extra space (for the three pointers).

# Code
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
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode curr = head;
        ListNode next;

        while (curr != null) {
            next = curr.next; // Store next node
            curr.next = prev; // Reverse current node's pointer to prev
            prev = curr;      // Move prev and curr pointers one step forward
            curr = next;
        }

        // prev is now the head of the reversed list
        return prev;
    }
}
```

