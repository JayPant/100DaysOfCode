### Intuition
To find the `rowIndex`-th row of Pascal's Triangle, we can generate all rows up to that row, leveraging the properties of Pascal's Triangle. Each element in the triangle is the sum of the two elements directly above it.

### Approach
1. **Generate Pascal's Triangle Up to the `rowIndex`-th Row:**
   - Use a nested loop to generate each row.
   - For each row, initialize the first and last elements as 1.
   - For the elements in between, calculate the value by summing the two elements from the previous row.

2. **Return the Desired Row:**
   - Once all rows up to the `rowIndex`-th row are generated, return the last row.

### Complexity
- **Time Complexity:** \(O(n^2)\) because generating each row involves summing elements from the previous row.
- **Space Complexity:** \(O(n^2)\) due to storing all rows up to the `rowIndex`-th row.

### Code
```java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<List<Integer>> pascal = new ArrayList<>();

        for (int i = 0; i <= rowIndex; i++) {
            List<Integer> row = new ArrayList<>();
            for (int j = 0; j <= i; j++) {
                if (j == 0 || j == i) {
                    row.add(1);
                } else {
                    row.add(pascal.get(i - 1).get(j - 1) + pascal.get(i - 1).get(j));
                }
            }
            pascal.add(row);
        }
        return pascal.get(rowIndex);
    }
}
```

### Explanation
1. **Outer Loop (Generating Each Row):**
   - Iterates from 0 to `rowIndex` to generate each row of Pascal's Triangle.

2. **Inner Loop (Generating Elements in Each Row):**
   - Iterates from 0 to the current row index `i` to generate the elements of the current row.
   - The first and last elements of each row are always 1.
   - The elements in between are calculated as the sum of the two elements directly above them from the previous row.

3. **Returning the Result:**
   - After generating all the rows, return the `rowIndex`-th row from the list of rows.

