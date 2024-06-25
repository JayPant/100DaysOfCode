# Intuition
To find the largest odd number, we start from the rightmost digit and move towards the left. As soon as we encounter an odd digit, we return the substring from the start of the number to that digit.

# Approach
1. Iterate through the digits of the input number from right to left.
2. For each digit, check if it's odd.
3. If we find an odd digit, return the substring from the start of the number to that digit.
4. If no odd digit is found, return an empty string.

# Complexity
- **Time complexity**: \(O(n)\), where \(n\) is the number of digits in the input number. The algorithm iterates through all the digits once.
- **Space complexity**: \(O(1)\). The algorithm uses only a constant amount of extra space.

# Code
```
class Solution {
    public String largestOddNumber(String num) {
        for (int i = num.length() - 1; i >= 0; i--) {
            if (Character.getNumericValue(num.charAt(i)) % 2 == 1) {
                return num.substring(0, i + 1);
            }
        }
        return "";        
    }
}
```