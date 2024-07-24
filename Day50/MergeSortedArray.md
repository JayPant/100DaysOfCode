# **Intuition**
The problem requires merging two sorted arrays where the first array has enough space to hold elements from the second array. We can achieve this by merging the arrays from the end to the beginning, which avoids overwriting elements in `nums1`.

# **Approach**
1. **Pointers Initialization:**
   - Initialize three pointers:
     - `i` pointing to the last element of the valid part of `nums1` (i.e., `m-1`).
     - `j` pointing to the last element of `nums2` (i.e., `n-1`).
     - `k` pointing to the last position in `nums1` (i.e., `m+n-1`).

2. **Merge Process:**
   - Iterate from the end of both arrays:
     - Compare elements pointed by `i` and `j`.
     - Place the larger element at position `k` in `nums1`.
     - Move the corresponding pointer (`i` or `j`) and the pointer `k` one step back.
   - If there are remaining elements in `nums2` (i.e., `j` is not yet `-1`), copy them to the beginning of `nums1`.

This ensures that all elements are correctly merged while maintaining sorted order.

# **Complexity**
- **Time Complexity:** $$O(n + m)$$, where \(n\) is the length of `nums2` and \(m\) is the number of valid elements in `nums1`. Each element is processed exactly once.
- **Space Complexity:** $$O(1)$$ since we are merging in-place and not using any extra space.

# **Code**
```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int i = m - 1;  // Pointer for nums1
        int j = n - 1;  // Pointer for nums2
        int k = m + n - 1;  // Pointer for the merged array

        // Merge from the end
        while (j >= 0) {
            if (i >= 0 && nums1[i] > nums2[j]) {
                nums1[k--] = nums1[i--];
            } else {
                nums1[k--] = nums2[j--];
            }
        }
    }
}
```
