

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
To solve the problem of finding the maximum twin sum in a linked list, we can use a two-pointer technique. The idea is to reverse the second half of the list and then compare pairs of values from the first half and the reversed second half.

# Approach
<!-- Describe your approach to solving the problem. -->
1. **Find the Middle**: Use the slow and fast pointer technique to find the middle of the linked list. The slow pointer moves one step at a time, while the fast pointer moves two steps.
2. **Reverse the Second Half**: Reverse the second half of the list starting from the middle node. This helps us in comparing the values from the first and second halves directly.
3. **Calculate Twin Sums**: Initialize two pointers, one at the start and one at the middle (start of the reversed second half). Calculate the sum of pairs of nodes (one from the first half and one from the reversed second half) and keep track of the maximum sum.

### Detailed Steps:
1. Use slow and fast pointers to find the middle of the linked list.
2. Reverse the second half of the list.
3. Initialize two pointers, `left` at the head and `right` at the start of the reversed second half.
4. Traverse both halves simultaneously, calculating the sum of pairs and updating the maximum sum.

# Complexity
- **Time complexity:**  
    $$O(n)$$ where \(n\) is the length of the linked list. We traverse the list a few times linearly.

- **Space complexity:**  
    $$O(1)$$ since we are using only a constant amount of extra space (pointers).

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
    public int pairSum(ListNode head) {
        ListNode slow = head;
        ListNode fast = head.next;

        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        ListNode mid = slow;
        ListNode prev = null;
        ListNode curr = mid.next;
        mid.next = null;
        ListNode next;

        while (curr != null) {
            next = curr.next;
            curr.next = prev;
            prev = curr;
            curr = next;
        }

        ListNode left = head, right = prev;
        int max = 0;

        while (left != null && right != null) {
            int sum = left.val + right.val;
            max = Math.max(sum, max);
            left = left.next;
            right = right.next;
        }
        return max;
    }
}
```

<details>
<summary>Python</summary>

```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def pairSum(self, head: ListNode) -> int:
        slow, fast = head, head.next
        
        # Find the middle of the linked list
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
        
        # Reverse the second half of the linked list
        prev, curr = None, slow.next
        slow.next = None
        while curr:
            next_node = curr.next
            curr.next = prev
            prev = curr
            curr = next_node
        
        left, right = head, prev
        max_sum = 0
        
        # Calculate the twin sums and find the maximum
        while right:
            max_sum = max(max_sum, left.val + right.val)
            left = left.next
            right = right.next
        
        return max_sum
```
</details>

<details>
<summary>C++</summary>

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */

class Solution {
public:
    int pairSum(ListNode* head) {
        ListNode* slow = head;
        ListNode* fast = head->next;
        
        // Find the middle of the linked list
        while (fast != nullptr && fast->next != nullptr) {
            slow = slow->next;
            fast = fast->next->next;
        }
        
        // Reverse the second half of the linked list
        ListNode* prev = nullptr;
        ListNode* curr = slow->next;
        slow->next = nullptr;
        while (curr != nullptr) {
            ListNode* next = curr->next;
            curr->next = prev;
            prev = curr;
            curr = next;
        }
        
        ListNode* left = head;
        ListNode* right = prev;
        int max_sum = 0;
        
        // Calculate the twin sums and find the maximum
        while (right != nullptr) {
            max_sum = std::max(max_sum, left->val + right->val);
            left = left->next;
            right = right->next;
        }
        
        return max_sum;
    }
};
```
</details>

---
