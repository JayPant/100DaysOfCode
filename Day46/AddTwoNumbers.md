
# Intuition
When we add two numbers represented as linked lists, we need to handle the addition digit by digit from the least significant digit to the most significant digit. This is akin to performing manual addition with a carry.

# Approach
1. Create a dummy head node to help simplify the code by avoiding edge cases.
2. Initialize a pointer `curr` to point to the dummy head and a variable `carry` to keep track of any carryover during addition.
3. Traverse both linked lists simultaneously, adding corresponding digits. If one list is shorter, treat missing values as 0.
4. For each pair of digits (including carry):
   - Calculate the sum of the current digits and the carry.
   - Update the carry for the next iteration.
   - Create a new node with the digit value (sum % 10) and link it to the current node.
   - Move the `curr` pointer to the next node.
5. After processing both lists, if there's any remaining carry, add a new node with the carry value.
6. Return the node next to the dummy head, which is the head of the resultant linked list.

# Complexity
- **Time complexity:**  
    $$O(n)$$ where \(n\) is the length of the longer list. Each node in the lists is processed exactly once.
- **Space complexity:**  
    $$O(n)$$ for the space used by the new list.

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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummyHead = new ListNode(0);
        ListNode curr = dummyHead;
        int carry = 0;

        while (l1 != null || l2 != null || carry != 0) {
            int x = (l1 != null) ? l1.val : 0;
            int y = (l2 != null) ? l2.val : 0;

            int sum = x + y + carry;
            carry = sum / 10;
            curr.next = new ListNode(sum % 10);
            curr = curr.next;

            if (l1 != null) l1 = l1.next;
            if (l2 != null) l2 = l2.next;
        }

        return dummyHead.next;
    }
}
```

