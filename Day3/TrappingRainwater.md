# Intuition
To solve the problem of trapping rainwater, we need to understand that the amount of water trapped at a particular index depends on the maximum heights to the left and right of that index. The trapped water is the difference between the minimum of these two maximum heights and the height at that index.

# Approach
Precompute Left Max Heights: Create an array leftMax where leftMax[i] stores the maximum height from the left up to index i.
Precompute Right Max Heights: Create an array rightMax where rightMax[i] stores the maximum height from the right up to index i.
Calculate Trapped Water: Iterate through the height array and compute the trapped water at each index as Math.min(leftMax[i], rightMax[i]) - height[i]. Sum these values to get the total trapped water.

# Complexity
Time complexity:
The time complexity is (O(n)) because we make three passes through the height array: one for computing leftMax, one for computing rightMax, and one for calculating the trapped water.

Space complexity:
The space complexity is (O(n)) due to the additional space required for the leftMax and rightMax arrays.

# Code

```java
class Solution {
    public int trap(int[] height) {
        int n = height.length;
        if (n == 0) return 0;
        
        int[] leftMax = new int[n];
        int[] rightMax = new int[n];

        leftMax[0] = height[0];
        for (int i = 1; i < n; i++) {
            leftMax[i] = Math.max(leftMax[i - 1], height[i]);
        }

        rightMax[n - 1] = height[n - 1];
        for (int i = n - 2; i >= 0; i--) {
            rightMax[i] = Math.max(rightMax[i + 1], height[i]);
        }

        int water = 0;
        for (int i = 0; i < n; i++) {
            water += Math.min(leftMax[i], rightMax[i]) - height[i];
        }

        return water;
    }
}
```