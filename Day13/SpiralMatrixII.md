# Intuition
The task requires us to fill an n x n matrix in a spiral order starting from the top-left corner and moving right initially. This involves repeatedly filling the matrix in the order: top row, right column, bottom row, and left column, until all elements are placed.

# Approach

Initialization: Create an n x n matrix initialized to zeros. Define the boundaries for rows (topRow and bottomRow) and columns (leftCol and rightCol).
Filling the Matrix:
Use a while loop to fill the matrix while element is less than or equal to n * n.
Top Row: Fill from left to right, then move the topRow boundary down.
Right Column: Fill from top to bottom, then move the rightCol boundary left.
Bottom Row: Fill from right to left, then move the bottomRow boundary up.
Left Column: Fill from bottom to top, then move the leftCol boundary right.
Termination: The loop terminates once all elements are filled in the matrix.

# Complexity

Time complexity:
O(n^2)
Each element is visited once in an n x n matrix.

Space complexity:
O(1)(excluding the space required to store the output) since we're modifying the matrix in place and only using a few additional variables for boundaries and counters.

# Code

```java
class Solution {
    public int[][] generateMatrix(int n) {
        int[][] matrix = new int[n][n];
        
        int topRow = 0, bottomRow = n - 1;
        int rightCol = n - 1;
        int leftCol = 0;
        int element = 1;

        while (element <= n * n) {
            // topRow -> leftCol to rightCol 
            for (int j = leftCol; j <= rightCol && element <= n * n; j++) {
                matrix[topRow][j] = element++;
            }
            topRow++;

            // rightCol -> topRow to bottomRow 
            for (int i = topRow; i <= bottomRow && element <= n * n; i++) {
                matrix[i][rightCol] = element++;
            }
            rightCol--;

            // bottomRow -> rightCol to leftCol 
            for (int j = rightCol; j >= leftCol && element <= n * n; j--) {
                matrix[bottomRow][j] = element++;
            }
            bottomRow--;

            // leftCol -> bottomRow to topRow 
            for (int i = bottomRow; i >= topRow && element <= n * n; i--) {
                matrix[i][leftCol] = element++;
            }
            leftCol++;
        }

        return matrix;
    }
}
```