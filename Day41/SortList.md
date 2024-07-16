

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
When asked to sort a linked list, one of the efficient ways to do so is by using the Merge Sort algorithm. This algorithm works well with linked lists because it doesn't require random access to elements.

# Approach
<!-- Describe your approach to solving the problem. -->
The idea is to:
1. **Divide the List**: Split the linked list into two halves using the slow and fast pointer technique to find the middle.
2. **Sort Each Half**: Recursively sort each half.
3. **Merge the Sorted Halves**: Merge the two sorted halves to produce the final sorted linked list.

### Steps:
1. **Finding the Middle**: Use two pointers, `slow` and `fast`. `slow` moves one step at a time, while `fast` moves two steps. When `fast` reaches the end, `slow` will be at the middle.
2. **Splitting the List**: Split the list into two halves from the middle.
3. **Recursive Sort**: Recursively sort both halves.
4. **Merge**: Merge the two sorted halves using a helper function.

# Complexity
- **Time complexity:**  
    $$O(n \log n)$$ because we are dividing the list into halves and then merging them, which takes linear time.

- **Space complexity:**  
    $$O(\log n)$$ due to the recursion stack space used by the sort function.

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

    private ListNode getMid(ListNode head) {
        ListNode slow = head;
        ListNode fast = head.next;

        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
    }

    public ListNode sortList(ListNode head) {
        if (head == null || head.next == null) return head;

        ListNode mid = getMid(head);
        ListNode rightHead = mid.next;
        mid.next = null;

        ListNode left = sortList(head);
        ListNode right = sortList(rightHead);

        return mergeTwoLists(left, right);
    }

    private ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode dummy = new ListNode(-1);
        ListNode current = dummy;

        while (list1 != null && list2 != null) {
            if (list1.val <= list2.val) {
                current.next = list1;
                list1 = list1.next;
            } else {
                current.next = list2;
                list2 = list2.next;
            }
            current = current.next;
        }

        if (list1 != null) {
            current.next = list1;
        } else {
            current.next = list2;
        }

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
    def getMid(self, head):
        slow, fast = head, head.next
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
        return slow

    def sortList(self, head):
        if not head or not head.next:
            return head

        mid = self.getMid(head)
        right_head = mid.next
        mid.next = None

        left = self.sortList(head)
        right = self.sortList(right_head)

        return self.mergeTwoLists(left, right)

    def mergeTwoLists(self, list1, list2):
        dummy = ListNode(-1)
        current = dummy

        while list1 and list2:
            if list1.val <= list2.val:
                current.next = list1
                list1 = list1.next
            else:
                current.next = list2
                list2 = list2.next
            current = current.next

        if list1:
            current.next = list1
        else:
            current.next = list2

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
 *     ListNode(int val) : val(val), next(nullptr) {}
 *     ListNode(int val, ListNode *next) : val(val), next(next) {}
 * };
 */

class Solution {
public:
    ListNode* getMid(ListNode* head) {
        ListNode* slow = head;
        ListNode* fast = head->next;

        while (fast != nullptr && fast->next != nullptr) {
            slow = slow->next;
            fast = fast->next->next;
        }
        return slow;
    }

    ListNode* sortList(ListNode* head) {
        if (head == nullptr || head->next == nullptr) return head;

        ListNode* mid = getMid(head);
        ListNode* rightHead = mid->next;
        mid->next = nullptr;

        ListNode* left = sortList(head);
        ListNode* right = sortList(rightHead);

        return mergeTwoLists(left, right);
    }

    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        ListNode dummy(-1);
        ListNode* current = &dummy;

        while (list1 != nullptr && list2 != nullptr) {
            if (list1->val <= list2->val) {
                current->next = list1;
                list1 = list1->next;
            } else {
                current->next = list2;
                list2 = list2->next;
            }
            current = current->next;
        }

        if (list1 != nullptr) {
            current->next = list1;
        } else {
            current->next = list2;
        }

        return dummy.next;
    }
};
```
</details>

---