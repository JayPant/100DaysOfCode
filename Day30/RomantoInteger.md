
# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The primary idea is to understand how Roman numerals work. In Roman numerals, certain smaller values placed before larger values signify subtraction (e.g., IV means 4). By scanning through the string of Roman numerals from left to right and keeping track of the current and next numerals, we can determine whether to add or subtract the current numeral's value.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Initialize a result variable to zero.
2. Iterate through the string of Roman numerals.
3. For each character in the string:
   - Get the integer value of the current numeral.
   - If it's not the last character and the value of the current numeral is less than the next numeral, subtract the current numeral's value from the result.
   - Otherwise, add the current numeral's value to the result.
4. Return the result after the loop completes.

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
The time complexity is $$O(n)$$ where n is the length of the string. This is because we are scanning through the string once.

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
The space complexity is $$O(1)$$ since we are using a constant amount of extra space.

# Code
```java
class Solution {
    public int romanToInt(String s) {
        if (s == null || s.length() == 0) {
            return 0;
        }

        int res = 0;
        for (int i = 0; i < s.length(); i++) {
            int currentVal = getValue(s.charAt(i));
            if (i < s.length() - 1) {
                int nextVal = getValue(s.charAt(i + 1));
                if (currentVal < nextVal) {
                    res -= currentVal;
                } else {
                    res += currentVal;
                }
            } else {
                res += currentVal;
            }
        }

        return res;
    }

    private int getValue(char romanChar) {
        switch (romanChar) {
            case 'I': return 1;
            case 'V': return 5;
            case 'X': return 10;
            case 'L': return 50;
            case 'C': return 100;
            case 'D': return 500;
            default: return 1000;
             
    }
}
```
