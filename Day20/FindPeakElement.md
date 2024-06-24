# Intuition
To find a peak element in an array, we can utilize a binary search approach to efficiently locate a peak by comparing mid elements and adjusting the search range accordingly. This method ensures that we can find a peak in \(O(\log n)\) time complexity.

# Approach
1. **Edge Cases**: 
   - If the array has only one element, return its index.
   - Check if the first or the last element is a peak element.
2. **Binary Search**:
   - Initialize `low` to 1 and `high` to `n-2` to exclude the already checked first and last elements.
   - Perform binary search:
     - Calculate the mid index.
     - If the element at `mid` is greater than both its neighbors, return `mid` as the peak index.
     - If the element at `mid` is greater than the element at `mid-1`, move `low` to `mid + 1`.
     - Otherwise, move `high` to `mid - 1`.
3. If no peak is found within the loop, the function returns `-1` (this should not happen given the problem constraints).

# Complexity
- **Time complexity**: \(O(\log n)\), due to binary search.
- **Space complexity**: \(O(1)\), as no extra space is used.

# Code
```java
class Solution {
    public int findPeakElement(int[] nums) {
        int n = nums.length;
        
        // Edge case: if there is only one element
        if (n == 1) return 0;
        
        // Check if the first or last element is a peak
        if (nums[0] > nums[1]) return 0;
        if (nums[n - 1] > nums[n - 2]) return n - 1;

        // Binary search between the second and the second last element
        int low = 1, high = n - 2;

        while (low <= high) {
            int mid = low + (high - low) / 2;

            // Check if mid is a peak
            if (nums[mid - 1] < nums[mid] && nums[mid] > nums[mid + 1])
                return mid;

            // If mid is greater than the previous element, move to the right half
            if (nums[mid] > nums[mid - 1]) {
                low = mid + 1;
            } else {
                // Else move to the left half
                high = mid - 1;
            }
        }

        // This line should never be reached if input guarantees a peak
        return -1;
    }
}
```
