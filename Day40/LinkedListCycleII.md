# Intuition
When trying to detect a cycle in a linked list, using two pointers (slow and fast) is effective. The fast pointer moves twice as fast as the slow pointer. If there is a cycle, the fast pointer will eventually meet the slow pointer within the cycle.

# Approach
1. **Initialize Two Pointers**: Start both slow and fast pointers at the head of the list.
2. **Cycle Detection**: Move the slow pointer one step and the fast pointer two steps at a time. If they meet, a cycle exists.
3. **Finding the Cycle Start**: After detecting a cycle, reset the slow pointer to the head. Move both pointers one step at a time. The node where they meet again will be the start of the cycle.

# Complexity
- **Time Complexity**: \(O(n)\), where \(n\) is the number of nodes in the linked list. Both pointers traverse the list a constant number of times.
- **Space Complexity**: \(O(1)\), as only two pointers are used.

### Code
```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode detectCycle(ListNode head) {
        if (head == null || head.next == null) {
            return null;
        }

        ListNode slow = head;
        ListNode fast = head;

        // First step: Detect if a cycle is present
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) {
                // Cycle detected, now find the start of the cycle
                slow = head;
                while (slow != fast) {
                    slow = slow.next;
                    fast = fast.next;
                }
                return slow; // Starting node of the cycle
            }
        }
        return null; // No cycle detected
    }
}
```

