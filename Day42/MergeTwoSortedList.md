

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The problem of merging two sorted linked lists can be tackled by comparing the nodes of both lists one by one and arranging them in ascending order in a new linked list. This way, we can efficiently merge the two lists without needing extra space, aside from a few pointers.

# Approach
<!-- Describe your approach to solving the problem. -->
1. **Create a Dummy Node**: Start by creating a dummy node to act as a placeholder for the result list. This helps simplify the code by avoiding special cases for the head of the list.
2. **Compare and Merge**: Use a pointer to iterate through both lists, adding the smaller node to the new list each time. Move the pointer in the list from which the node was added.
3. **Attach Remaining Nodes**: Once one list is exhausted, simply attach the remaining nodes of the other list to the new list.

### Detailed Steps:
1. Initialize a `dummy` node and a `temp` pointer pointing to `dummy`.
2. While both lists are not empty, compare the current nodes of both lists. Add the smaller node to the result list and move the pointer forward in the list from which the node was taken.
3. If one of the lists is empty, attach the remaining nodes of the other list to the result list.
4. Return the merged list starting from the node next to `dummy`.

# Complexity
- **Time complexity:**  
    $$O(n + m)$$ where \(n\) and \(m\) are the lengths of the two linked lists. We traverse each list once.

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
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode dummy = new ListNode(-1);
        ListNode temp = dummy;

        while (list1 != null && list2 != null) {
            if (list1.val <= list2.val) {
                temp.next = list1;
                list1 = list1.next;
            } else {
                temp.next = list2;
                list2 = list2.next;
            }
            temp = temp.next;
        }

        // Attach remaining nodes, if any
        if (list1 != null) {
            temp.next = list1;
        } else {
            temp.next = list2;
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
    def mergeTwoLists(self, list1: ListNode, list2: ListNode) -> ListNode:
        dummy = ListNode(-1)
        temp = dummy

        while list1 and list2:
            if list1.val <= list2.val:
                temp.next = list1
                list1 = list1.next
            else:
                temp.next = list2
                list2 = list2.next
            temp = temp.next

        # Attach remaining nodes, if any
        if list1:
            temp.next = list1
        else:
            temp.next = list2

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
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        ListNode dummy(-1);
        ListNode* temp = &dummy;

        while (list1 && list2) {
            if (list1->val <= list2->val) {
                temp->next = list1;
                list1 = list1->next;
            } else {
                temp->next = list2;
                list2 = list2->next;
            }
            temp = temp->next;
        }

        // Attach remaining nodes, if any
        if (list1) {
            temp->next = list1;
        } else {
            temp->next = list2;
        }

        return dummy.next;
    }
};
```
</details>

