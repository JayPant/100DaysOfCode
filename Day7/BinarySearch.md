# Intuition
When tasked with finding the position of a target element in a sorted array, my first thought was to use the binary search algorithm. Binary search is well-suited for sorted arrays and is much more efficient than a linear search due to its logarithmic time complexity.

# Approach
To solve this problem, I implemented the binary search algorithm with the following steps:

Initialize two pointers, low and high, to the beginning and end of the array, respectively.
While the low pointer is less than or equal to the high pointer:
Calculate the middle index mid.
If the element at mid is the target, return mid.
If the element at mid is less than the target, move the low pointer to mid + 1.
If the element at mid is greater than the target, move the high pointer to mid - 1.
If the loop ends without finding the target, return -1 indicating the target is not in the array.
This approach efficiently narrows down the search range by half with each iteration, making it much faster than checking each element sequentially.

# Complexity
Time complexity: O(log⁡n), where (n) is the number of elements in the array, because the search range is halved with each iteration.
Space complexity: O(1), as no extra space is used except for a few variables.

# Code

```java
class Solution {
    public int search(int[] arr, int target) {
        int low = 0;
        int high = arr.length - 1;

        while (low <= high) {
            int mid = low + (high - low) / 2;

            if (arr[mid] == target) {
                return mid;
            }

            if (arr[mid] < target) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }

        return -1;
    }
}
```