# Intuition
To search for a target value in a 2D matrix, we can start from the top-right corner of the matrix. Since the matrix is sorted in ascending order both row-wise and column-wise, this approach allows us to efficiently move towards the target value by making decisions based on comparisons with the current element.

# Approach
Start from the top-right corner of the matrix.
While the current position is within the bounds of the matrix:
If the current element is equal to the target, return true.
If the target is less than the current element, move left to explore smaller elements.
If the target is greater than the current element, move down to explore larger elements.
If the target is not found after iterating through the matrix, return false.


# Complexity
Time complexity: (O(m + n)), where (m) is the number of rows and (n) is the number of columns in the matrix.
Space complexity: (O(1))

# Code

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int row = 0;
        int col = matrix[0].length - 1;

        while (row < matrix.length && col >= 0) {
            if (matrix[row][col] == target) {
                return true;
            } else if (target < matrix[row][col]) {
                col--;
            } else {
                row++;
            }
        }

        return false;
    }
}
```