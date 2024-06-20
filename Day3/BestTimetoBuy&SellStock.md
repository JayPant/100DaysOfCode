# Intuition
The key idea is to iterate through the list of stock prices, keeping track of the minimum price encountered so far and calculating the potential profit at each step by comparing the current price with the minimum price. This way, we can keep updating the maximum profit.

# Approach
Initialize two variables: buyPrice to Integer.MAX_VALUE to keep track of the minimum price encountered so far, and profitMax to 0 to keep track of the maximum profit.
Iterate through the list of stock prices:
If the current price is less than buyPrice, update buyPrice to the current price.
Otherwise, calculate the potential profit by subtracting buyPrice from the current price and update profitMax if the potential profit is greater than the current profitMax.
Return profitMax.

# Complexity
Time complexity:
The time complexity is (O(n)) because we iterate through the list of prices once.

Space complexity:
The space complexity is (O(1)) because we only use a few extra variables regardless of the input size.

# Code

```java
class Solution {
    public int maxProfit(int[] prices) {
        int buyPrice = Integer.MAX_VALUE;
        int profitMax = 0;

        for(int i = 0; i < prices.length; i++) {
            if (buyPrice < prices[i]) {
                int profit = prices[i] - buyPrice;
                profitMax = Math.max(profit, profitMax);
            } else {
                buyPrice = prices[i];
            }
        }

        return profitMax;
    }
}
```