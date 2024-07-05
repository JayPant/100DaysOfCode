# Intuition
The goal is to modify the array in-place such that all instances of the specified value `val` are removed, and return the new length of the array without those elements.

# Approach
1. **Initialization**: Start with a variable `k` to keep track of the position where non-`val` elements should be placed.
2. **Iterate through the array**: Use a loop to traverse each element of the array.
3. **Check for `val`**: If the current element is not equal to `val`, move it to position `k` in the array and increment `k`.
4. **Return the new length**: `k` will represent the new length of the modified array, where all instances of `val` have been removed.

# Complexity
- **Time complexity**: \(O(n)\), where \(n\) is the length of the input array `nums`. Each element is processed once.
- **Space complexity**: \(O(1)\). The function operates in-place and uses only a constant amount of extra space.

# Code
```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int k = 0; // Initialize the position to place non-val elements
        
        // Traverse through the array
        for (int i = 0; i < nums.length; i++) {
            // If current element is not val, move it to position k
            if (nums[i] != val) {
                nums[k++] = nums[i];
            }
        }
        
        return k; // Return the new length of the modified array
    }
}
```
