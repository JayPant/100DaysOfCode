# Intuition
The problem requires finding two numbers in the array that add up to the target value. The brute force way to solve this would be to check all pairs of numbers to see if their sum equals the target.

# Approach
Iterate through the array with two nested loops.
For each element in the outer loop, iterate through the elements that come after it using the inner loop.
Check if the sum of the two elements equals the target.
If a pair is found that satisfies the condition, return their indices as a result.
If no such pair is found after checking all possible pairs, return an empty array indicating no solution.

# Complexity
Time complexity:
O(n^2), where ( n ) is the length of the array. This is because we are using two nested loops to check all possible pairs of elements in the array.

Space complexity:
O(1), as we are only using a constant amount of extra space for the indices and the result array.

# Code

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int n = nums.length;
        for (int i = 0; i < n - 1; i++) {
            for (int j = i + 1; j < n; j++) {
                if (nums[i] + nums[j] == target) {
                    return new int[]{i, j};
                }
            }
        }
        return new int[]{}; // No solution found
    }
}
```