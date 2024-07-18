
# Intuition
The problem is to reverse a sublist of a linked list from position `left` to `right`. The first thought is to identify the starting point of the sublist, reverse the sublist, and then reconnect the reversed sublist back to the original list.

# Approach
1. Use a dummy node to handle edge cases easily.
2. Traverse the list to find the node just before the `left` position (`leftPrev`) and the node at the `left` position (`curr`).
3. Reverse the sublist from `left` to `right`.
4. Reconnect the reversed sublist back to the original list.
5. Return the new head of the list.

# Complexity
- **Time complexity:**  
    $$O(n)$$ where \(n\) is the number of nodes in the linked list. We traverse the list a couple of times.

- **Space complexity:**  
    $$O(1)$$ since we only use a few pointers for the operations.

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
    public ListNode reverseBetween(ListNode head, int left, int right) {
        if (head == null || left == right) return head;

        ListNode dummy = new ListNode(-1);
        dummy.next = head;
        ListNode leftPrev = dummy;
        ListNode curr = head;

        for (int i = 0; i < left - 1; i++) {
            leftPrev = leftPrev.next;
            curr = curr.next;
        }

        ListNode prev = null;
        ListNode subListHead = curr;
        
        for (int i = 0; i <= right - left; i++) {
            ListNode next = curr.next;
            curr.next = prev;
            prev = curr;
            curr = next;
        }

        leftPrev.next = prev;
        subListHead.next = curr;

        return dummy.next;
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
    def reverseBetween(self, head: ListNode, left: int, right: int) -> ListNode:
        if not head or left == right:
            return head

        dummy = ListNode(-1)
        dummy.next = head
        left_prev = dummy
        curr = head

        for _ in range(left - 1):
            left_prev = left_prev.next
            curr = curr.next

        prev = None
        sublist_head = curr

        for _ in range(right - left + 1):
            next_node = curr.next
            curr.next = prev
            prev = curr
            curr = next_node

        left_prev.next = prev
        sublist_head.next = curr

        return dummy.next
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
    ListNode* reverseBetween(ListNode* head, int left, int right) {
        if (!head || left == right) return head;

        ListNode dummy(-1);
        dummy.next = head;
        ListNode* leftPrev = &dummy;
        ListNode* curr = head;

        for (int i = 0; i < left - 1; ++i) {
            leftPrev = leftPrev->next;
            curr = curr->next;
        }

        ListNode* prev = nullptr;
        ListNode* subListHead = curr;

        for (int i = 0; i <= right - left; ++i) {
            ListNode* next = curr->next;
            curr->next = prev;
            prev = curr;
            curr = next;
        }

        leftPrev->next = prev;
        subListHead->next = curr;

        return dummy.next;
    }
};
```
</details>
