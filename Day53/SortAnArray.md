### Intuition
The problem is to sort an array of integers. The first thought is to use an efficient and well-known sorting algorithm like merge sort, which is suitable for this problem because of its divide-and-conquer approach that ensures a stable and efficient sorting process.

### Approach
1. **Divide the Array:**
   - The array is recursively divided into two halves until each subarray contains a single element or no elements.

2. **Merge the Sorted Halves:**
   - The sorted halves are merged back together in a way that ensures the merged array is sorted.

3. **Merge Sort Algorithm:**
   - Recursively sort the left half of the array.
   - Recursively sort the right half of the array.
   - Merge the two sorted halves.

### Complexity
- **Time Complexity:** \(O(n \log n)\) because the array is repeatedly divided in half and then merged.
- **Space Complexity:** \(O(n)\) due to the temporary array used for merging.

### Code
```java
class Solution {
    public int[] sortArray(int[] nums) {
        int start = 0, end = nums.length - 1;
        sort(nums, start, end);
        return nums;
    }

    private void sort(int[] nums, int start, int end) {
        if (start >= end) return;

        int mid = start + (end - start) / 2;

        sort(nums, start, mid);
        sort(nums, mid + 1, end);
        merge(nums, start, mid, end);
    }

    private void merge(int[] nums, int start, int mid, int end) {
        int[] temp = new int[end - start + 1];
        int i = start, j = mid + 1, idx = 0;

        while (i <= mid && j <= end) {
            if (nums[i] <= nums[j]) {
                temp[idx++] = nums[i++];
            } else {
                temp[idx++] = nums[j++];
            }
        }

        while (i <= mid) {
            temp[idx++] = nums[i++];
        }

        while (j <= end) {
            temp[idx++] = nums[j++];
        }

        for (i = start; i <= end; i++) {
            nums[i] = temp[i - start];
        }
    }
}
```

### Explanation
1. **sortArray Function:**
   - Initializes the sorting process by calling the `sort` function with the entire array range.

2. **sort Function:**
   - Base case: If the start index is greater than or equal to the end index, the function returns because the subarray is already sorted.
   - Recursively sorts the left half and the right half of the array.
   - Merges the two sorted halves using the `merge` function.

3. **merge Function:**
   - Uses a temporary array to merge the two sorted halves.
   - Compares elements from both halves and adds the smaller element to the temporary array.
   - After one of the halves is exhausted, the remaining elements from the other half are added to the temporary array.
   - Copies the merged and sorted elements back to the original array.

