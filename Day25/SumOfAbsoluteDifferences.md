

# Intuition
The goal is to compute the sum of absolute differences between each element in the sorted array `nums` and all other elements. Given the sorted property, we can leverage prefix and suffix sums to efficiently calculate these differences.

# Approach
1. **Prefix Sums**: Calculate prefix sums, where `prefixSum[i]` represents the sum of elements from the start of the array to index `i`.
2. **Suffix Sums**: Calculate suffix sums, where `suffixSum[i]` represents the sum of elements from index `i` to the end of the array.
3. **Result Calculation**: For each element `nums[i]`, compute the sum of absolute differences using the prefix and suffix sums:
   - The difference with all previous elements can be derived from the prefix sum.
   - The difference with all subsequent elements can be derived from the suffix sum.
4. **Formula**:
   - For each `i`, the sum of differences is given by:
     - `leftDiff = nums[i] * i - prefixSum[i - 1]` (if `i > 0`)
     - `rightDiff = suffixSum[i + 1] - nums[i] * (n - i - 1)` (if `i < n - 1`)
   - Combine these to get the total sum of absolute differences for `nums[i]`.

# Complexity
- Time complexity: \(O(n)\), where \(n\) is the length of the array. We make a single pass through the array to compute prefix and suffix sums, and another pass to compute the result.
- Space complexity: \(O(n)\), for storing the prefix and suffix sums.

# Code
```java
class Solution {
    public int[] getSumAbsoluteDifferences(int[] nums) {
        int n = nums.length;
        int[] result = new int[n];
        int[] prefixSum = new int[n];
        int[] suffixSum = new int[n];
        
        // Compute prefix sums
        prefixSum[0] = nums[0];
        for (int i = 1; i < n; i++) {
            prefixSum[i] = prefixSum[i - 1] + nums[i];
        }
        
        // Compute suffix sums
        suffixSum[n - 1] = nums[n - 1];
        for (int i = n - 2; i >= 0; i--) {
            suffixSum[i] = suffixSum[i + 1] + nums[i];
        }
        
        // Calculate the result for each element
        for (int i = 0; i < n; i++) {
            int leftSum = (i > 0) ? prefixSum[i - 1] : 0;
            int rightSum = (i < n - 1) ? suffixSum[i + 1] : 0;
            
            int leftCount = i;
            int rightCount = n - i - 1;
            
            int leftDiff = nums[i] * leftCount - leftSum;
            int rightDiff = rightSum - nums[i] * rightCount;
            
            result[i] = leftDiff + rightDiff;
        }
        
        return result;
    }

    public static void main(String[] args) {
        Solution solution = new Solution();
        int[] nums1 = {2, 3, 5};
        int[] result1 = solution.getSumAbsoluteDifferences(nums1);
        System.out.println(Arrays.toString(result1)); // Output: [4, 3, 5]

        int[] nums2 = {1, 4, 6, 8, 10};
        int[] result2 = solution.getSumAbsoluteDifferences(nums2);
        System.out.println(Arrays.toString(result2)); // Output: [24, 15, 13, 15, 21]
    }
}
```

### Explanation:
1. **Prefix and Suffix Sums**:
   - `prefixSum[i]` contains the sum of all elements from `nums[0]` to `nums[i]`.
   - `suffixSum[i]` contains the sum of all elements from `nums[i]` to `nums[n-1]`.

2. **Result Calculation**:
   - For each element `nums[i]`, compute the sum of absolute differences with all elements to the left and to the right using the prefix and suffix sums.
   - `leftDiff` accounts for differences with elements to the left.
   - `rightDiff` accounts for differences with elements to the right.

3. **Efficiency**:
   - The solution processes the array in linear time, making it efficient for large inputs.
