# Intuition
To solve this problem, we can use the first row and first column of the matrix as markers. We iterate through the matrix and use the first cell of each row and column to mark whether that row or column should be set to zero.

# Approach
We initialize two boolean variables, firstRow and firstCol, to keep track of whether the first row and first column should be set to zero.
We iterate through the matrix and use the first cell of each row and column to mark whether that row or column should be set to zero. If we encounter a zero, we set the first cell of its row and column to zero.
We iterate through the matrix again, starting from the second row and second column, and use the marks in the first row and column to set the zeros.
Finally, if firstRow is true, we set the entire first row to zeros. If firstCol is true, we set the entire first column to zeros.


# Complexity
Time complexity: (O(m \times n)), where (m) is the number of rows and (n) is the number of columns in the matrix.
Space complexity: (O(1))


# Code

```java
public class Solution {
    public void setZeroes(int[][] matrix) {
        boolean firstRow = false, firstCol = false;

        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[0].length; j++) {
                if (matrix[i][j] == 0) {
                    if (i == 0) firstRow = true;
                    if (j == 0) firstCol = true;
                    matrix[0][j] = 0;
                    matrix[i][0] = 0;
                }
            }
        }

        for (int i = 1; i < matrix.length; i++) {
            for (int j = 1; j < matrix[0].length; j++) {
                if (matrix[i][0] == 0 || matrix[0][j] == 0) {
                    matrix[i][j] = 0;
                }
            }
        }

        if (firstRow) {
            for (int j = 0; j < matrix[0].length; j++) {
                matrix[0][j] = 0;
            }
        }

        if (firstCol) {
            for (int i = 0; i < matrix.length; i++) {
                matrix[i][0] = 0;
            }
        }
    }
}
```