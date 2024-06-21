# Intuition
The problem requires finding the single non-duplicate element in a sorted array where every element appears twice except for one. Since the array is sorted, we can leverage binary search to achieve an efficient solution.

# Approach
Initial Checks:

If the array has only one element, return that element.
If the first element is different from the second, return the first element.
If the last element is different from the second to last, return the last element.
Binary Search:

Initialize low to 1 and high to n-2 to exclude the already checked first and last elements.
Perform binary search:
Calculate mid as the average of low and high.
Check if nums[mid] is the single non-duplicate element by comparing it to its neighbors.
Adjust the search range based on the pattern observed:
If mid is even and nums[mid] is equal to nums[mid + 1], the single element must be on the right.
If mid is odd and nums[mid] is equal to nums[mid - 1], the single element must also be on the right.
Otherwise, it must be on the left.


# Complexity
Time complexity:
The binary search approach ensures a time complexity of (O(\log n)).

Space complexity:
The algorithm uses constant space, so the space complexity is (O(1)).

# Code

```java
class Solution {
    public int singleNonDuplicate(int[] nums) {
        int n = nums.length;
        
        // Edge case checks
        if (n == 1) return nums[0];
        if (nums[0] != nums[1]) return nums[0];
        if (nums[n - 1] != nums[n - 2]) return nums[n - 1];
        
        // Binary search initialization
        int low = 1, high = n - 2;
        
        while (low <= high) {
            int mid = (low + high) / 2;
            
            // Check if the mid element is the single non-duplicate
            if (nums[mid] != nums[mid + 1] && nums[mid] != nums[mid - 1]) {
                return nums[mid];
            }
            
            // Adjust search range based on the pattern
            if ((mid % 2 == 0 && nums[mid] == nums[mid + 1]) || (mid % 2 == 1 && nums[mid] == nums[mid - 1])) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
        
        return -1; // This line should never be reached
    }
}
```













