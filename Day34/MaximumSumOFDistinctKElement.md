# Intuition
To solve the problem of finding the maximum sum of a subarray of size `k` with all unique elements, we need to efficiently manage and check the uniqueness of elements in a sliding window of size `k`.

# Approach
The approach involves using a sliding window technique with a HashSet:
1. Use two pointers (`i` and `j`) to represent the current window `[i, j-1]`.
2. Use a `HashSet` (`set`) to keep track of unique elements within the current window.
3. Expand the window by moving the `j` pointer to the right, adding elements to `set` and updating `currSum`.
4. Once the size of `set` reaches `k`, check if `currSum` is greater than `maxSum` and update `maxSum` accordingly.
5. Slide the window by moving the `i` pointer to the right, removing elements from `set` and subtracting them from `currSum`.

# Complexity
- Time complexity: **O(n)**, where `n` is the length of the `nums` array. Each element is processed at most twice (once when adding and once when removing from the `set`), making the time complexity linear.
- Space complexity: **O(k)** in the worst case, where `k` is the size of the `HashSet` storing unique elements in the window.

# Code
```java
class Solution {
    public long maximumSubarraySum(int[] nums, int k) {
        long maxSum = 0, currSum = 0;
        HashSet<Integer> set = new HashSet<>();
        int i = 0, j = 0;
        
        while (i < nums.length) {
            // Filling the HashSet with unique elements until we have size k or reach end
            while (j < nums.length && set.size() < k && !set.contains(nums[j])) {
                set.add(nums[j]);
                currSum += nums[j];
                j++;
            }
            
            // Checking if we have a valid k-sized window
            if (set.size() == k) {
                maxSum = Math.max(currSum, maxSum);
            }
            
            // Move the window forward by removing nums[i] from the current window
            currSum -= nums[i];
            set.remove(nums[i]);
            i++;
        }
        
        return maxSum;
    }
}
```
