# Intuition
When solving the problem of finding the first and last positions of a target in a sorted array, the sorted nature of the array suggests the use of binary search. Binary search can efficiently narrow down the search space to find the desired positions in logarithmic time.

# Approach
Find the First Position:

Use a binary search to locate the first occurrence of the target.
If nums[mid] == target, update the first position and continue searching in the left half by adjusting the right pointer.
If nums[mid] < target, move the left pointer to mid + 1.
If nums[mid] > target, move the right pointer to mid - 1.
Find the Last Position:

Reset the left and right pointers to the start and end of the array, respectively.
Use another binary search to locate the last occurrence of the target.
If nums[mid] == target, update the last position and continue searching in the right half by adjusting the left pointer.
If nums[mid] < target, move the left pointer to mid + 1.
If nums[mid] > target, move the right pointer to mid - 1.
Return the Result:

Return an array containing the first and last positions of the target.

# Complexity
Time complexity: O(log n)
We perform binary search twice, each taking O(log n) time.
Space complexity: O(1)
We only use a constant amount of extra space for the pointers and result array.


# Code
```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int left = 0, right = nums.length - 1;
        int first = -1, last = -1;

        // Find the first occurrence
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] < target) {
                left = mid + 1;
            } else if (nums[mid] > target) {
                right = mid - 1;
            } else {
                first = mid;
                right = mid - 1;  // continue searching in the left half
            }
        }

        // Reset the pointers for the second search
        left = 0;
        right = nums.length - 1;

        // Find the last occurrence
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] < target) {
                left = mid + 1;
            } else if (nums[mid] > target) {
                right = mid - 1;
            } else {
                last = mid;
                left = mid + 1;  // continue searching in the right half
            }
        }

        return new int[] {first, last};
    }
}
```