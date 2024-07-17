
# Intuition
When two linked lists intersect, they share some common nodes at the end. To find the intersection point, we need to identify the common part in both linked lists.

# Approach
1. **Use Two Pointers**: Initialize two pointers, one for each linked list.
2. **Traverse Both Lists**: Move each pointer to the next node in its respective list. If a pointer reaches the end of its list, move it to the head of the other list.
3. **Find Intersection**: Continue this process until the two pointers meet. The meeting point is the intersection node, or `null` if the lists do not intersect.

### Detailed Steps:
1. Initialize two pointers, `listA` and `listB`, at the heads of the two lists.
2. Traverse both lists simultaneously. When a pointer reaches the end of its list, redirect it to the head of the other list.
3. If the lists intersect, the pointers will meet at the intersection node after traversing both lists fully. If they do not intersect, both pointers will reach `null` at the same time.

# Complexity
- **Time complexity:**  
    $$O(m + n)$$ where \(m\) and \(n\) are the lengths of the two linked lists. We traverse each list twice at most.

- **Space complexity:**  
    $$O(1)$$ since we are using only a constant amount of extra space (pointers).

# Code

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if (headA == null || headB == null) return null;
        
        ListNode listA = headA;
        ListNode listB = headB;
        
        while (listA != listB) {
            listA = listA == null ? headB : listA.next;
            listB = listB == null ? headA : listB.next;
        }
        
        return listA;
    }
}
```

<details>
<summary>Python</summary>

```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None

class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> ListNode:
        if not headA or not headB:
            return None
        
        listA, listB = headA, headB
        
        while listA != listB:
            listA = headB if listA is None else listA.next
            listB = headA if listB is None else listB.next
            
        return listA
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
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        if (headA == nullptr || headB == nullptr) return nullptr;
        
        ListNode* listA = headA;
        ListNode* listB = headB;
        
        while (listA != listB) {
            listA = listA == nullptr ? headB : listA->next;
            listB = listB == nullptr ? headA : listB->next;
        }
        
        return listA;
    }
};
```
</details>
