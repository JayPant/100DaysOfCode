# **Intuition**
The task requires swapping the values of the k-th node from the beginning with the k-th node from the end of the list. This can be achieved by first determining the size of the linked list, then identifying the nodes at these positions, and finally swapping their values.

# **Approach**
1. **Calculate the Size of the Linked List:**
   - Traverse the list to determine its length.

2. **Find the k-th Node from the Beginning:**
   - Traverse the list again up to the k-th node from the start.

3. **Find the k-th Node from the End:**
   - Traverse the list up to the (size - k + 1)-th node from the start, which is equivalent to the k-th node from the end.

4. **Swap the Values:**
   - Swap the values of the nodes found in steps 2 and 3.


# **Complexity**
- **Time Complexity:** $$O(n)$$ where \(n\) is the length of the list. We traverse the list twice.
- **Space Complexity:** $$O(1)$$ as we use only a few pointers and variables.

# **Code**
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
    public ListNode swapNodes(ListNode head, int k) {
        // Step 1: Calculate the size of the linked list
        int size = 0;
        ListNode temp = head;
        while (temp != null) {
            size++;
            temp = temp.next;
        }

        // Step 2: Find the k-th node from the beginning
        ListNode first = head;
        for (int i = 1; i < k; i++) {
            first = first.next;
        }

        // Step 3: Find the k-th node from the end
        ListNode second = head;
        for (int i = 1; i <= size - k; i++) {
            second = second.next;
        }

        // Step 4: Swap the values of the first and second nodes
        int tempVal = first.val;
        first.val = second.val;
        second.val = tempVal;

        return head;
    }
}
```

