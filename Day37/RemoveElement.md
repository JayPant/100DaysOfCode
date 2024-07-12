
# Intuition
To solve the problem of removing all nodes from a linked list that contain a specific value, a good approach is to use a dummy node. This simplifies handling edge cases, such as removing the head node.

# Approach
1. **Create a Dummy Node**: Initialize a dummy node that points to the head of the list. This dummy node helps in easily handling cases where the head node itself needs to be removed.
2. **Traverse the List**: Use a pointer initialized to the dummy node to traverse the linked list.
3. **Remove Nodes**: While traversing the list, check if the value of the next node equals the given value. If it does, skip this node by updating the pointer's `next` to `next.next`. Otherwise, move the pointer to the next node.
4. **Return the New Head**: After traversing and removing the necessary nodes, the new head of the list will be `dummy.next`.

# Complexity
- **Time complexity**: 
  - $$O(n)$$, where \( n \) is the number of nodes in the linked list. This is because we traverse the entire list once.
- **Space complexity**: 
  - $$O(1)$$, as we only use a constant amount of extra space for the dummy node and the pointer.

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
    public ListNode removeElements(ListNode head, int val) {
        // Create a dummy node that points to the head of the list
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        
        // Initialize a temp pointer to traverse the list
        ListNode temp = dummy;
        
        // Traverse the list
        while (temp.next != null) {
            if (temp.next.val == val) {
                // If the value matches, skip the node
                temp.next = temp.next.next;
            } else {
                // Otherwise, move to the next node
                temp = temp.next;
            }
        }
        
        // Return the new head of the list
        return dummy.next;
    }
}
```

