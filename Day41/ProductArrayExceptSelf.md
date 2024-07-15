
# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The problem requires calculating the product of all the elements in the array except for the current element without using division. My first thought is to use additional arrays to keep track of the products to the left and right of each element, then combine these products to get the desired result.

# Approach
<!-- Describe your approach to solving the problem. -->
1. **Left Product Array**: Create an array where each element at index `i` contains the product of all elements to the left of `i`.
2. **Right Product Array**: Similarly, create an array where each element at index `i` contains the product of all elements to the right of `i`.
3. **Combine**: Multiply the corresponding elements of the left and right product arrays to get the final result.

In the optimized approach:
1. Initialize the result array with the left products directly.
2. Iterate from the end of the array to update the result array with the right products, thus saving space.

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$$O(n)$$ - We traverse the array a constant number of times.

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$$O(1)$$ - Apart from the output array, we use only a few additional variables, making the extra space usage constant.

# Code
```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        int[] ans = new int[n];

        // Initialize the result array with left products
        ans[0] = 1;
        for (int i = 1; i < n; i++) {
            ans[i] = ans[i - 1] * nums[i - 1];
        }

        // Update the result array with right products
        int right = 1;
        for (int i = n - 1; i >= 0; i--) {
            ans[i] = ans[i] * right;
            right *= nums[i];
        }

        return ans;
    }
}
```

