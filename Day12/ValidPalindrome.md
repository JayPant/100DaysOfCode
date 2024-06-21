# Intuition
To determine if a given string is a palindrome, we need to compare characters from the beginning and end of the string moving towards the center. However, we need to ignore non-alphanumeric characters and consider uppercase and lowercase letters as equal.

# Approach
Initialize Pointers: Start with two pointers, left at the beginning and right at the end of the string.
Skip Non-Alphanumeric Characters: Move the left pointer to the right until it points to an alphanumeric character. Similarly, move the right pointer to the left until it points to an alphanumeric character.
Compare Characters: If the characters at the left and right pointers are not equal (ignoring case), return false.
Move Pointers: If the characters are equal, move both pointers towards the center and repeat the process.
Completion: If the pointers meet or cross each other without finding any mismatch, return true.

# Complexity
Time Complexity: O(n), where (n) is the length of the string. Each character is processed at most once.

Space Complexity: O(1). No extra space is required beyond the input string and a few variables.
Code

```java
class Solution {
    public boolean isPalindrome(String s) {
        // Initialize pointers
        int left = 0;
        int right = s.length() - 1;

        while (left < right) {
            // Move the left pointer to the next alphanumeric character
            while (left < right && !Character.isLetterOrDigit(s.charAt(left))) {
                left++;
            }

            // Move the right pointer to the previous alphanumeric character
            while (left < right && !Character.isLetterOrDigit(s.charAt(right))) {
                right--;
            }

            // Compare the characters at the left and right pointers
            if (Character.toLowerCase(s.charAt(left)) != Character.toLowerCase(s.charAt(right))) {
                return false;
            }

            // Move both pointers towards the center
            left++;
            right--;
        }

        return true;
    }
}
```