# Intuition
Pascal's Triangle is constructed by starting with a single 1 at the top. Each subsequent row is built by adding adjacent elements from the previous row, with 1s on the ends. This pattern ensures that each number is the sum of the two numbers directly above it.

# Approach
Initialization: Create a List<List<Integer>> to store the rows of Pascal's Triangle.
Building the Triangle:
Loop through numRows, where each iteration represents a row in the triangle.
For each row, create a List<Integer> to hold the elements.
Populate the row:
The first and last elements are always 1.
For the elements in between, use the sum of the two elements directly above from the previous row.
Add the constructed row to the main list.
Return the Triangle: After constructing all rows, return the list of lists representing Pascal's Triangle.


# Complexity
Time complexity:
O(n^2)
Each row has a number of elements proportional to its row index, leading to a total of 1 + 2 + 3 + ... + n = n(n + 1)/2 operations.

Space complexity:
O(n^2)
The space required to store the entire triangle, which consists of n rows with an increasing number of elements.

# Code

```java
import java.util.*;

class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> pascal = new ArrayList<>();
        
        for (int i = 0; i < numRows; i++) {
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
        
        return pascal;
    }

}
```