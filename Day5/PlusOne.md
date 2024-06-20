# Intuition
When faced with the problem of incrementing a large integer represented as an array of digits, my first thought was to simulate the process of addition as we do by hand. Starting from the least significant digit, we handle the carry and propagate it to the more significant digits if needed.

# Approach
To solve this problem, I iterated through the array from the end to the beginning. For each digit:

If the digit is less than 9, I simply increment it by one and return the array since no further carry propagation is needed.
If the digit is 9, I set it to 0 and continue to the next digit.
If all digits are 9 (e.g., [9, 9, 9]), after the loop, I create a new array with an extra length and set the first element to 1, resulting in [1, 0, 0, 0].

# Complexity
Time complexity: O(n), where (n) is the length of the digits array, since we potentially need to iterate through all digits.
Space complexity: O(n) in the worst case when we need to create a new array of length (n+1).
Code

```java
class Solution {
    public int[] plusOne(int[] digits) {
        for (int i = digits.length - 1; i >= 0; i--) {
            if (digits[i] < 9) {
                digits[i]++;
                return digits;
            }
            digits[i] = 0;
        }

        digits = new int[digits.length + 1];
        digits[0] = 1;
        return digits;
    }
}
```