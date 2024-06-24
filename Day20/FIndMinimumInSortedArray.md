# Intuition
The minimum element in a rotated sorted array is the pivot point where the rotation occurred. In a fully sorted array, this would be the first element. By leveraging binary search, we can efficiently find this pivot point even in a rotated array.

# Approach
1. **Initialization**: Start with `low` pointing to the beginning of the array and `high` pointing to the end. Initialize `min` to a very large value.
2. **Binary Search**: Use binary search to narrow down the position of the minimum element:
   - Compute the mid index.
   - Compare the elements at `low` and `mid`:
     - If the left part (`nums[low]` to `nums[mid]`) is sorted, the minimum element must be either at `low` or in the right part. Update `min` with the minimum value found so far and move `low` to `mid + 1`.
     - If the right part (`nums[mid]` to `nums[high]`) is sorted, the minimum element is either at `mid` or in the left part. Update `min` and move `high` to `mid - 1`.
3. **Termination**: When `low` exceeds `high`, the minimum value found during the search is returned.

# Complexity
- **Time complexity**: \(O(\log n)\), since we are using binary search to divide the search space in half each time.
- **Space complexity**: \(O(1)\), as no extra space is used.

# Code
```java
class Solution {
    public int findMin(int[] nums) {
        int low = 0, high = nums.length - 1;
        int min = Integer.MAX_VALUE;

        while (low <= high) {
            int mid = low + (high - low) / 2;

            if (nums[low] <= nums[mid]) {
                // Left part is sorted
                min = Math.min(min, nums[low]);
                low = mid + 1;
            } else {
                // Right part is sorted
                min = Math.min(min, nums[mid]);
                high = mid - 1;
            }
        }
        return min;
    }
}
```
.