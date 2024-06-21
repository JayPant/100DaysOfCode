# Intuition
The first thought is to iterate through the matrix and sum up the elements of the primary and secondary diagonals. For the primary diagonal, we add the elements where the row index equals the column index. For the secondary diagonal, we add the elements where the row index and the column index sum up to the size of the matrix minus one. We need to be careful not to double-count the center element in matrices of odd size.

# Approach

Initialize a variable sum to zero to store the sum of the diagonal elements.
Loop through each row i of the matrix:
Add the element at the primary diagonal position mat[i][i] to sum.
If i is not equal to mat.length - 1 - i (to avoid double-counting the central element in odd-sized matrices), add the element at the secondary diagonal position mat[i][mat.length - 1 - i] to sum.
Return the sum after iterating through all the rows.


# Complexity
Time complexity: ( O(n) ), where ( n ) is the number of rows (or columns) in the matrix. This is because we loop through the matrix only once.
Space complexity: ( O(1) ), as we are using a constant amount of extra space.

# Code

```java
class Solution {
    public int diagonalSum(int[][] mat) {
        int sum = 0;
        for (int i = 0; i < mat.length; i++) {
            // Add the primary diagonal element
            sum += mat[i][i];

            // Add the secondary diagonal element if it's not the same as the primary diagonal element
            if (i != mat.length - 1 - i) {
                sum += mat[i][mat.length - 1 - i];
            }
        }
        return sum;
    }
}
```