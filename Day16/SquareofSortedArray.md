
# Intuition

The problem requires squaring each element in a sorted array and then returning a new array of the squares, also sorted. Squaring negative numbers could disrupt the original order, so we need to handle the order carefully.

# Approach

Square each element: The first step is to square each element in the array. Squaring is straightforward but will make all numbers non-negative.
Two-pointer technique: After squaring, the smallest elements could be in the middle if the original array had both negative and positive numbers. To handle this, use two pointers:
One starting from the beginning (left) and the other from the end (right) of the squared array.
Compare the elements at both pointers, placing the larger element in the current position (k) of the result array.
Move the pointers inward, and decrease the position k of the result array.
This ensures that the largest squares are placed at the end of the result array, maintaining a sorted order.

# Complexity
Time complexity: (O(n)), where (n) is the number of elements in the array. This is because we iterate through the array twice, once to square the elements and once to sort them using the two-pointer technique.
Space complexity: (O(n)), where (n) is the size of the input array. This is due to the additional array used to store the result.


# Code

```java
class Solution {
    public int[] sortedSquares(int[] nums) {
        // Step 1: Square each element in the array
        for (int i = 0; i < nums.length; i++) {
            nums[i] = nums[i] * nums[i];
        }

        // Step 2: Use two-pointer technique to sort the squares
        int left = 0, right = nums.length - 1;
        int k = nums.length - 1;
        int[] ans = new int[nums.length];

        while (left <= right) {
            if (nums[left] > nums[right]) {
                ans[k--] = nums[left];
                left++;
            } else {
                ans[k--] = nums[right];
                right--;
            }
        }
        return ans;
    }
}```