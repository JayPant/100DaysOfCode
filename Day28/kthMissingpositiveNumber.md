# Intuition
The problem can be efficiently solved using binary search. The key idea is to determine the number of missing numbers up to each element in the array. By comparing the number of missing numbers to \( k \), we can adjust our search range and find the k-th missing number.

## Approach
1. **Initialize Variables:** Start with two pointers, `low` at the beginning of the array and `high` at the end of the array.
2. **Binary Search:** Use a while loop to perform the binary search.
    - Calculate the middle index `mid`.
    - Calculate the number of missing numbers up to `arr[mid]`, which is `arr[mid] - (mid + 1)`.
    - If the number of missing numbers is less than `k`, it means the k-th missing number is to the right of `mid`, so move the `low` pointer to `mid + 1`.
    - If the number of missing numbers is greater than or equal to `k`, it means the k-th missing number is to the left of or at `mid`, so move the `high` pointer to `mid - 1`.
3. **Return Result:** After the loop terminates, `low` will be the position in the array where the number of missing numbers is just less than or equal to `k`. The k-th missing number is `low + k`.

## Complexity
- **Time complexity:** \( O(\log n) \), because binary search is being used.
- **Space complexity:** \( O(1) \), since no additional space proportional to the input size is used.

## Code
```java
class Solution {
    public int findKthPositive(int[] arr, int k) {
        int low = 0, high = arr.length - 1;

        while (low <= high) {
            int mid = low + (high - low) / 2;
            int missing = arr[mid] - (mid + 1);

            if (missing < k) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }

        return low + k;
    }
}
```