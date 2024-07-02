## Intuition
When you first think about this problem, you realize that it's a variant of the classical binary search problem. The goal is to find the smallest element that is strictly greater than the target. Since the array is sorted, binary search is an efficient approach.

## Approach
1. **Initialize Variables:** Start with two pointers, `low` at the beginning of the array and `high` at the end of the array. Also, initialize `ans` to the first element of the array as a fallback.
2. **Binary Search:** Use a while loop to perform the binary search.
    - Calculate the middle index `mid`.
    - If the middle element is greater than the target, it could be a potential answer, so update `ans` to this middle element and move the `high` pointer to `mid - 1` to look for a smaller potential answer.
    - If the middle element is less than or equal to the target, move the `low` pointer to `mid + 1` to look for a larger element.
3. **Return Result:** After the loop terminates, `ans` will hold the smallest element greater than the target.

## Complexity
- **Time complexity:** $$O(\log n)$$, because binary search is being used.
- **Space complexity:** $$O(1)$$, since no additional space proportional to the input size is used.

## Code
```java
class Solution {
    public char nextGreatestLetter(char[] letters, char target) {
        int low = 0, high = letters.length - 1;
        char ans = letters[0];

        while (low <= high) {
            int mid = low + (high - low) / 2;

            if (letters[mid] > target) {
                ans = letters[mid];
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return ans;
    }
}
```

