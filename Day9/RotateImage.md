# Intuition
To rotate a matrix by 90 degrees clockwise, we can perform two steps:

Transpose the matrix: Convert rows to columns.
Reverse each row: This will result in the rotated matrix.

# Approach
Transpose the matrix:
Swap the element at position ((i, j)) with the element at position ((j, i)) for all (i < j). This effectively converts rows into columns.
Reverse each row:
After transposing, reverse each row to complete the 90-degree clockwise rotation.

# Complexity
Time complexity:

Transposing the matrix takes (O(n^2)) time, where (n) is the number of rows (or columns) in the matrix.
Reversing each row takes (O(n^2)) time as well since there are (n) rows, each of length (n).
Thus, the overall time complexity is (O(n^2)).
Space complexity:

The space complexity is (O(1)) as we are modifying the matrix in place without using any extra space.

# Code

```java
class Solution {
    static void transpose(int[][] matrix) {
        for (int i = 0; i < matrix.length; i++) {
            for (int j = i; j < matrix[0].length; j++) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }
    }
    
    static void reverse(int[] arr) {
        int left = 0, right = arr.length - 1;

        while (left < right) {
            int temp = arr[left];
            arr[left] = arr[right];
            arr[right] = temp;
            left++;
            right--;
        }
    }

    public void rotate(int[][] matrix) {
        transpose(matrix);

        for (int i = 0; i < matrix.length; i++) {
            reverse(matrix[i]);
        }
    }
}
```