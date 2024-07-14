# Intuition
To determine if a linked list has a cycle, using two pointers (slow and fast) is a straightforward and efficient approach. The fast pointer moves at twice the speed of the slow pointer. If there is a cycle, the fast pointer will eventually meet the slow pointer.

# Approach
1. **Initialize Two Pointers**: Start both slow and fast pointers at the head of the list.
2. **Traverse the List**: Move the slow pointer one step at a time and the fast pointer two steps at a time.
3. **Check for Meeting Point**: If the fast pointer meets the slow pointer, a cycle is present.
4. **End of List Check**: If the fast pointer reaches the end of the list (i.e., `fast` or `fast.next` is `null`), there is no cycle.

# Complexity
- **Time Complexity**: \(O(n)\), where \(n\) is the number of nodes in the linked list. In the worst case, both pointers traverse the list linearly.
- **Space Complexity**: \(O(1)\), as only two pointers are used, regardless of the size of the linked list.

# Code
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
    public boolean hasCycle(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;

        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;

            if (slow == fast) {
                return true;
            }
        }
        return false;
    }
}
```

 