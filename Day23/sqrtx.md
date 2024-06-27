# Intuition
My first thought is to use binary search to find the square root of a number efficiently. Given that the problem involves finding an integer square root, binary search can quickly narrow down the range of possible values.

# Approach
1. **Base Case**: If the input `x` is less than 2, return `x` directly since the square root of `0` is `0` and the square root of `1` is `1`.
2. **Binary Search**:
   - Initialize `low` to `0` and `high` to `x`.
   - Use a while loop to repeatedly narrow down the search range.
   - Calculate `mid` as the average of `low` and `high`.
   - Compute `mid * mid` and compare it with `x`:
     - If `mid * mid` equals `x`, return `mid`.
     - If `mid * mid` is less than `x`, move the `low` boundary up and set `root` to `mid`.
     - If `mid * mid` is greater than `x`, move the `high` boundary down.
3. **Return the Result**: After the loop completes, `root` will contain the largest integer such that `root * root <= x`.

# Complexity
- Time complexity: $$O(\log{x})$$. The binary search algorithm divides the search range by half each iteration.
- Space complexity: $$O(1)$$. The algorithm uses a constant amount of extra space.

# Code
```java
class Solution {
    public int mySqrt(int x) {
        if (x < 2) return x;

        int low = 0, high = x, root = 0;

        while (low <= high) {
            int mid = low + (high - low) / 2;

            long midSquared = (long) mid * mid; 

            if (midSquared == x) return mid;

            if (midSquared < x) {
                low = mid + 1;
                root = mid;
            } else {
                high = mid - 1;
            }
        }

        return root;
    }
}
```