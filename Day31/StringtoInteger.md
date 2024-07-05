# Intuition
The goal of the `myAtoi` function is to convert a string to an integer, handling various edge cases such as leading whitespace, optional signs, non-digit characters, and overflow.

# Approach
1. **Initialize variables**: `index` to traverse the string, `sign` to store the number's sign.
2. **Handle empty string**: If the string is empty, return 0.
3. **Skip leading whitespace**: Traverse through any leading whitespace characters.
4. **Handle optional sign**: Check if the current character is a '+' or '-', and update `sign` accordingly.
5. **Convert characters to integer**: Traverse through digit characters, updating the result.
6. **Handle overflow**: Check for overflow by comparing the result before and after multiplication/addition.

# Complexity
- **Time complexity**: \(O(n)\), where \(n\) is the length of the string.
- **Space complexity**: \(O(1)\), as we only use a few extra variables.

# Code for String to Integer (atoi)
```java
class Solution {
    public int myAtoi(String s) {
        int index = 0, sign = 1; // Step 1: Initialize variables
        
        if (s.length() == 0) return 0; // Step 2: Handle empty string

        // Step 3: Skip leading whitespace
        while (index < s.length() && s.charAt(index) == ' ') {
            index++;
        }

        // Step 4: Handle optional sign
        if (index < s.length() && (s.charAt(index) == '+' || s.charAt(index) == '-')) {
            sign = s.charAt(index) == '+' ? 1 : -1;
            index++;
        }

        int result = 0; // Initialize result

        // Step 5: Convert characters to integer
        while (index < s.length()) {
            if (!Character.isDigit(s.charAt(index))) break;

            char current = s.charAt(index++);
            int previous = result;

            result *= 10; // Step 6: Update result

            // Step 7: Handle overflow
            if (result / 10 != previous) {
                return sign == -1 ? Integer.MIN_VALUE : Integer.MAX_VALUE;
            }

            result += (current - '0');

            // Another overflow check (shouldn't be necessary but added for safety)
            if (result < 0) {
                return sign == -1 ? Integer.MIN_VALUE : Integer.MAX_VALUE;
            }
        }

        return result * sign; // Step 8: Return final result
    }
}
```
