## Intuition
The problem is about sorting an array of 0s, 1s, and 2s in a single pass with a linear time complexity. This can be efficiently solved using the Dutch National Flag algorithm by Edsger Dijkstra, which partitions the array into three sections: all 0s, all 1s, and all 2s.

## Approach
1. **Three Pointers**: Use three pointers:
   - `l` (left) to keep track of the position where the next 0 should go.
   - `m` (middle) to traverse the array.
   - `h` (high) to keep track of the position where the next 2 should go.
2. **Traverse the Array**: Iterate through the array with the middle pointer `m`:
   - If `nums[m] == 0`, swap it with `nums[l]` and increment both `l` and `m`.
   - If `nums[m] == 1`, simply move to the next element by incrementing `m`.
   - If `nums[m] == 2`, swap it with `nums[h]` and decrement `h` (do not increment `m` because the swapped element needs to be checked).

## Complexity
- **Time Complexity**: The algorithm runs in \(O(n)\) time, where \(n\) is the number of elements in the array, since each element is processed at most once.
- **Space Complexity**: The algorithm uses \(O(1)\) additional space, as it only uses a few extra variables for the pointers.

## Code
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