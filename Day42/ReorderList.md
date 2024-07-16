# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
When asked to reorder a linked list, the task is to rearrange it such that the nodes are in a specific sequence: the first node, followed by the last node, then the second node, followed by the second last node, and so on. To achieve this, we need to split the list into two halves, reverse the second half, and then merge the two halves in the desired order.

# Approach
<!-- Describe your approach to solving the problem. -->
The approach can be broken down into three main steps:
1. **Find the Middle**: Use the slow and fast pointer technique to find the middle of the linked list.
2. **Reverse the Second Half**: Reverse the second half of the list starting from the middle.
3. **Merge Two Halves**: Merge the two halves by alternating nodes from each half.

### Steps:
1. **Finding the Middle**: Use two pointers, `slow` and `fast`. `slow` moves one step at a time, while `fast` moves two steps. When `fast` reaches the end, `slow` will be at the middle.
2. **Reversing the Second Half**: Reverse the list starting from the node after the middle.
3. **Merging Two Halves**: Merge nodes from the first half and the reversed second half alternately.

# Complexity
- **Time complexity:**  
    $$O(n)$$ because we go through the list a few times linearly.

- **Space complexity:**  
    $$O(1)$$ as we are only using a constant amount of extra space.

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
    public void reorderList(ListNode head) {
        ListNode slow = head;
        ListNode fast = head.next;

        // Find the middle of the list
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        // Split and reverse the second half
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

        // Merge the two halves
        ListNode left = head;
        ListNode right = prev;
        ListNode nextL, nextR;

        while (left != null && right != null) {
            nextL = left.next;
            left.next = right;
            nextR = right.next;
            right.next = nextL;

            left = nextL;
            right = nextR;
        }
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
    def reorderList(self, head):
        if not head:
            return
        
        # Find the middle of the list
        slow, fast = head, head.next
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
        
        # Split and reverse the second half
        mid = slow
        prev, curr = None, mid.next
        mid.next = None
        while curr:
            next = curr.next
            curr.next = prev
            prev = curr
            curr = next
        
        # Merge the two halves
        left, right = head, prev
        while right:
            nextL = left.next
            left.next = right
            nextR = right.next
            right.next = nextL

            left = nextL
            right = nextR
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
 *     ListNode(int val) : val(val), next(nullptr) {}
 *     ListNode(int val, ListNode *next) : val(val), next(next) {}
 * };
 */

class Solution {
public:
    void reorderList(ListNode* head) {
        if (!head) return;

        // Find the middle of the list
        ListNode* slow = head;
        ListNode* fast = head->next;
        while (fast && fast->next) {
            slow = slow->next;
            fast = fast->next->next;
        }

        // Split and reverse the second half
        ListNode* mid = slow;
        ListNode* prev = nullptr;
        ListNode* curr = mid->next;
        mid->next = nullptr;
        while (curr) {
            ListNode* next = curr->next;
            curr->next = prev;
            prev = curr;
            curr = next;
        }

        // Merge the two halves
        ListNode* left = head;
        ListNode* right = prev;
        while (right) {
            ListNode* nextL = left->next;
            left->next = right;
            ListNode* nextR = right->next;
            right->next = nextL;

            left = nextL;
            right = nextR;
        }
    }
};
```
</details>
