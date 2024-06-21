# Intuition

To find a target in a 2D matrix where each row is sorted in ascending order and each row starts with a value greater than the last value of the previous row, we can treat the matrix as a flattened sorted array. This allows us to perform binary search efficiently.

# Approach
Matrix as a Single Array: Treat the 2D matrix as a 1D array. The matrix of size m x n can be imagined as a single sorted list.

Binary Search:
Initialize left to 0 and right to m * n - 1.
Calculate the middle index and convert it to the corresponding row and column indices in the matrix.
Compare the middle element with the target:
If equal, return true.
If less, move left to mid + 1.
If greater, move right to mid - 1.
Return Result: If the loop completes without finding the target, return false.

# Complexity

Time Complexity: (O(\log(m \times n))), where (m) is the number of rows and (n) is the number of columns, because we are performing binary search on m * n elements.

Space Complexity: (O(1)), as no additional space is required beyond the input matrix and a few variables.


# Code

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        if (matrix == null || matrix.length == 0 || matrix[0].length == 0) {
            return false;
        }

        int m = matrix.length;
        int n = matrix[0].length;
        int left = 0;
        int right = m * n - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;
            int midValue = matrix[mid / n][mid % n];

            if (midValue == target) {
                return true;
            } else if (midValue < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return false;
    }
}
```