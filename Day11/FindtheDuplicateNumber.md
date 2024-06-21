
# Intuition
The first thought is to recognize that the problem can be approached using cycle detection. The array represents a linked list where each value points to the next index. Given that there is a duplicate number, this linked list must have a cycle. Floyd's Tortoise and Hare algorithm is ideal for detecting cycles in linked lists with constant space complexity.

# Approach
Phase 1: Finding the Intersection Point

Use two pointers, slow and fast.
Initialize both pointers to the start of the array.
Move slow pointer by one step and fast pointer by two steps.
Continue until they meet. The meeting point indicates a cycle.
Phase 2: Finding the Entrance to the Cycle

Reset one pointer (slow) to the start of the array.
Move both pointers one step at a time until they meet again.
The meeting point is the entrance to the cycle, which is the duplicate number.

# Complexity
Time complexity: ( O(n) ), where ( n ) is the number of elements in the array. This is because both pointers traverse the array and the operations inside the loop are constant time.
Space complexity: ( O(1) ). We use only a constant amount of extra space for the pointers.

# Code

```java
class Solution {
    public int findDuplicate(int[] nums) {
        // Phase 1: Finding the intersection point of the two pointers
        int slow = nums[0];
        int fast = nums[0];
        do {
            slow = nums[slow];
            fast = nums[nums[fast]];
        } while (slow != fast);

        // Phase 2: Finding the entrance to the cycle
        slow = nums[0];
        while (slow != fast) {
            slow = nums[slow];
            fast = nums[fast];
        }

        // The entrance to the cycle is the duplicate number
        return slow;
    }
}
```