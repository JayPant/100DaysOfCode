# Intuition
When adding two non-negative numbers represented as strings, the approach is similar to manual addition performed from right to left. This involves summing corresponding digits from both strings, managing carry, and building the resulting number.

# Approach
1. Initialize a `StringBuilder` to build the resulting string.
2. Initialize `carry` to 0 for handling the carry-over in addition.
3. Use two pointers, `i` and `j`, starting from the end of `num1` and `num2` respectively.
4. Loop until both pointers are exhausted and there is no carry left:
   - Add the current digits from `num1` and `num2` to the `sum` along with the `carry`.
   - Calculate the new digit to append (`sum % 10`) and update the `carry` (`sum / 10`).
   - Move the pointers to the left.
5. Reverse the `StringBuilder` and convert it to a string to get the final result.

# Complexity
- **Time complexity:** \( O(\max(m, n)) \)
  - We traverse the longer of the two strings.
- **Space complexity:** \( O(\max(m, n)) \)
  - The space used by the `StringBuilder` to store the result.

# Code
```java
class Solution {
    public String addStrings(String num1, String num2) {
        StringBuilder str = new StringBuilder();
        int carry = 0;
        int i = num1.length() - 1, j = num2.length() - 1;

        while (i >= 0 || j >= 0 || carry != 0) {
            int sum = carry;
            if (i >= 0) {
                sum += num1.charAt(i--) - '0';
            }

            if (j >= 0) {
                sum += num2.charAt(j--) - '0';
            }

            str.append(sum % 10);
            carry = sum / 10;
        }

        return str.reverse().toString();
    }
}
```

