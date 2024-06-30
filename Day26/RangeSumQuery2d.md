# Intuition
The first thought is to iterate through the specified submatrix and sum up all the elements within the given boundaries. This brute-force approach directly accesses each element in the specified region and adds them together.

# Approach
1. **Initialization**: Store the matrix as an instance variable during the instantiation of the `NumMatrix` object.
2. **Summing Region**: In the `sumRegion` method, iterate through the rows and columns within the specified boundaries and sum the elements.

# Complexity
- **Time complexity**: 
  - The time complexity is \(O((row2 - row1 + 1) \times (col2 - col1 + 1))\). This is because in the worst case, we have to iterate through every element in the submatrix defined by the boundaries \((row1, col1)\) to \((row2, col2)\).

- **Space complexity**: 
  - The space complexity is \(O(1)\), as we are only using a fixed amount of additional space for storing the sum and loop variables, regardless of the input size.

# Code
```java
class NumMatrix {
    int[][] matrix;

    public NumMatrix(int[][] matrix) {
        this.matrix = matrix;
    }

    public int sumRegion(int row1, int col1, int row2, int col2) {
        int sum = 0;
        for (int i = row1; i <= row2; i++) {
            for (int j = col1; j <= col2; j++) {
                sum += matrix[i][j];
            }
        }
        return sum;
    }
}

/**
 * Your NumMatrix object will be instantiated and called as such:
 * NumMatrix obj = new NumMatrix(matrix);
 * int param_1 = obj.sumRegion(row1, col1, row2, col2);
 */
```