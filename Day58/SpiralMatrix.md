## Intuition
The problem requires us to traverse a matrix in a spiral order, starting from the top-left corner and moving towards the center. The intuition is to iteratively traverse the matrix layer by layer, starting from the outermost layer and moving inwards.

## Approach
1. **Initialization**:
   - Determine the number of rows (`r`) and columns (`c`) in the matrix.
   - Define four boundaries: `topRow`, `bottomRow`, `leftCol`, and `rightCol` to keep track of the edges of the current layer being traversed.
   - Initialize a list to store the elements in spiral order.

2. **Traversing the Matrix**:
   - Use a while loop that continues until all elements have been added to the list. The conditions `topRow <= bottomRow` and `leftCol <= rightCol` ensure that we are still within the bounds of the matrix.
   - For each iteration, follow these steps:
     - Traverse from `leftCol` to `rightCol` along `topRow` and then increment `topRow`.
     - Traverse from `topRow` to `bottomRow` along `rightCol` and then decrement `rightCol`.
     - Traverse from `rightCol` to `leftCol` along `bottomRow` and then decrement `bottomRow`.
     - Traverse from `bottomRow` to `topRow` along `leftCol` and then increment `leftCol`.

3. **Stopping Condition**:
   - The loop exits when `elements` equals the total number of elements in the matrix (`r * c`).

## Complexity
- **Time Complexity**: \(O(n \cdot m)\)
  - Where `n` is the number of rows and `m` is the number of columns. Each element in the matrix is visited exactly once.

- **Space Complexity**: \(O(1)\)
  - Apart from the output list, we use only a constant amount of extra space.

## Code
```java
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        int r = matrix.length, c = matrix[0].length;
        int topRow = 0, bottomRow = r - 1;
        int leftCol = 0, rightCol = c - 1;
        int elements = 0;

        List<Integer> list = new LinkedList<>();
        while (elements < r * c) {

            // topRow => leftCol -> rightCol
            for (int j = leftCol; j <= rightCol && elements < r * c; j++) {
                list.add(matrix[topRow][j]);
                elements++;
            }
            topRow++;

            // rightCol => topRow -> bottomRow
            for (int i = topRow; i <= bottomRow && elements < r * c; i++) {
                list.add(matrix[i][rightCol]);
                elements++;
            }
            rightCol--;

            // bottomRow => rightCol -> leftCol
            for (int j = rightCol; j >= leftCol && elements < r * c; j--) {
                list.add(matrix[bottomRow][j]);
                elements++;
            }
            bottomRow--;

            // leftCol => bottomRow -> topRow
            for (int i = bottomRow; i >= topRow && elements < r * c; i--) {
                list.add(matrix[i][leftCol]);
                elements++;
            }
            leftCol++;
        }

        return list;
    }
}
```

