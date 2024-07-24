
# **Intuition**
To efficiently calculate the sum of elements in a given range multiple times, we can use a prefix sum approach. The idea is to preprocess the array so that each element at index `i` contains the sum of elements from the start up to index `i`. This allows us to compute the sum of any subarray in constant time.

# **Approach**
1. **Preprocessing Step:**
   - Create a prefix sum array where each element at index `i` contains the sum of elements from the start of the array up to index `i`.
   - Iterate through the given array, updating each element to be the sum of itself and the previous elements.

2. **Query Step:**
   - For a given range `[i, j]`, the sum can be computed as:
     - `prefix[j]` if `i` is `0`.
     - `prefix[j] - prefix[i-1]` otherwise.
   - This allows us to answer each sum range query in constant time.

# **Complexity**
- **Time Complexity:**
  - **Preprocessing:** $$O(n)$$, where \(n\) is the length of the array.
  - **Query:** $$O(1)$$ for each sum range query.
- **Space Complexity:** $$O(n)$$ for storing the prefix sums.

# **Code**
```java
class NumArray {
    int[] nums;

    public NumArray(int[] nums) {
        // Preprocessing: compute prefix sums
        for (int i = 1; i < nums.length; i++) {
            nums[i] += nums[i - 1];
        }
        this.nums = nums;
    }

    public int sumRange(int i, int j) {
        // If the range starts from the beginning
        if (i == 0) {
            return nums[j];
        }
        // Otherwise, subtract the prefix sum up to i-1 from the prefix sum up to j
        return nums[j] - nums[i - 1];
    }
}

/**
 * Your NumArray object will be instantiated and called as such:
 * NumArray obj = new NumArray(nums);
 * int param_1 = obj.sumRange(left,right);
 */
```
