# Intuition
The problem requires finding a combination of three numbers from an array whose sum is closest to a given target. The first thought is to use a brute force approach by trying all possible combinations of three numbers, but this would be inefficient for large arrays. Instead, we can use a sorted array and the two-pointer technique to efficiently find the closest sum.

# Approach
1. **Sort the Array**: Sorting the array helps in efficiently finding the closest sum using the two-pointer technique.
2. **Initialize Closest Sum**: Initialize the closest sum with the sum of the first three numbers.
3. **Iterate with Two Pointers**:
   - For each element `nums[i]` in the array, use two pointers, `j` starting from `i + 1` and `k` starting from the end of the array.
   - Calculate the sum of the triplet `nums[i] + nums[j] + nums[k]`.
   - If this sum is closer to the target than the previously recorded closest sum, update the closest sum.
   - Adjust the pointers based on the comparison of the current sum with the target:
     - If the sum is less than the target, increment the left pointer `j` to get a larger sum.
     - If the sum is greater than the target, decrement the right pointer `k` to get a smaller sum.
4. **Return the Closest Sum**: After iterating through all elements and adjusting pointers, the closest sum is returned.

# Complexity
- **Time complexity**: Sorting the array takes \(O(n \log n)\) time. The nested loop runs in \(O(n^2)\) time, making the overall time complexity \(O(n^2)\).
- **Space complexity**: The space complexity is \(O(1)\) as we are not using any extra space proportional to the input size.

# Code
```java
class Solution {
    public int threeSumClosest(int[] nums, int target) {
        Arrays.sort(nums);
        int closestSum = nums[0] + nums[1] + nums[2];

        for (int i = 0; i < nums.length - 2; i++) {
            int j = i + 1;
            int k = nums.length - 1;

            while (j < k) {
                int sum = nums[i] + nums[j] + nums[k];
                if (Math.abs(sum - target) < Math.abs(closestSum - target)) {
                    closestSum = sum;
                }
                if (sum < target) {
                    j++;
                } else {
                    k--;
                }
            }
        }

        return closestSum;
    }
}
```
