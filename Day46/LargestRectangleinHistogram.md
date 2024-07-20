# Intuition
The problem of finding the largest rectangle in a histogram can be approached by leveraging the concept of the next smaller elements to the left and right of each bar. By identifying these boundaries, we can determine the maximum possible area for a rectangle formed by each bar as the shortest bar in the rectangle.

# Approach
1. **Identify the Next Smaller Elements:** For each bar, find the next smaller element on the left (`nsl`) and the next smaller element on the right (`nsr`).
2. **Compute the Width of Rectangles:** Use the positions of `nsl` and `nsr` to compute the width of the largest rectangle that each bar can form.
3. **Calculate the Maximum Area:** Iterate through each bar and calculate the area using its height and the width computed from the `nsl` and `nsr` arrays. Track the maximum area encountered.

Steps:
1. Traverse the histogram from right to left to compute the `nsr` array.
2. Traverse the histogram from left to right to compute the `nsl` array.
3. Calculate the area for each bar using the formula: `height[i] * (nsr[i] - nsl[i] - 1)`.
4. Return the maximum area found.

# Complexity
- **Time complexity:**  
    $$O(n)$$ for traversing the histogram to compute the `nsl` and `nsr` arrays and calculating the areas.
- **Space complexity:**  
    $$O(n)$$ for storing the `nsl` and `nsr` arrays and the stack.

# Code
```java
import java.util.Stack;

class Solution {
    public int largestRectangleArea(int[] heights) {
        int n = heights.length;
        int[] nsl = new int[n];
        int[] nsr = new int[n];
        int maxArea = 0;

        Stack<Integer> s = new Stack<>();

        // Compute the next smaller right (nsr)
        for (int i = n - 1; i >= 0; i--) {
            while (!s.isEmpty() && heights[s.peek()] >= heights[i]) {
                s.pop();
            }
            nsr[i] = s.isEmpty() ? n : s.peek();
            s.push(i);
        }

        s.clear();
        
        // Compute the next smaller left (nsl)
        for (int i = 0; i < n; i++) {
            while (!s.isEmpty() && heights[s.peek()] >= heights[i]) {
                s.pop();
            }
            nsl[i] = s.isEmpty() ? -1 : s.peek();
            s.push(i);
        }

        // Calculate the maximum area
        for (int i = 0; i < n; i++) {
            int width = nsr[i] - nsl[i] - 1;
            int area = heights[i] * width;
            maxArea = Math.max(maxArea, area);
        }

        return maxArea;
    }
}
```

