# Intuition
When sorting an array of 0s, 1s, and 2s, the first thought that comes to mind is to count the occurrences of each element and then recreate the array. However, a more optimal approach can be taken using the Dutch National Flag algorithm, which sorts the array in a single pass with constant space.

# Approach
The Dutch National Flag algorithm sorts the array by maintaining three pointers:
1. `l` (left) which tracks the position of the last sorted 0.
2. `m` (middle) which is the current element under examination.
3. `h` (high) which tracks the position of the first sorted 2.

The algorithm works as follows:
1. Initialize `l` to 0, `m` to 0, and `h` to the last index of the array.
2. Iterate through the array with `m`:
   - If the element at `m` is 0, swap it with the element at `l` and increment both `l` and `m`.
   - If the element at `m` is 1, just move `m` to the next element.
   - If the element at `m` is 2, swap it with the element at `h` and decrement `h`.
3. Repeat the process until `m` exceeds `h`.

This approach ensures that all 0s are moved to the beginning, all 2s are moved to the end, and all 1s remain in the middle.

# Complexity
- Time complexity:
The time complexity of this algorithm is $$O(n)$$, where $$n$$ is the number of elements in the array. This is because we process each element at most once.

- Space complexity:
The space complexity is $$O(1)$$ as we are only using a constant amount of extra space for the pointers.

# Code
```java
class Solution {

    private void swap(int[] nums, int a, int b) {
        int temp = nums[a];
        nums[a] = nums[b];
        nums[b] = temp;
    }

    public void sortColors(int[] nums) {
        int l = 0, m = 0, h = nums.length - 1;

        while (m <= h) {
            if (nums[m] == 0) {
                swap(nums, l, m);
                l++;
                m++;
            } else if (nums[m] == 1) {
                m++;
            } else {
                swap(nums, m, h);
                h--;
            }
        }
    }
}
```