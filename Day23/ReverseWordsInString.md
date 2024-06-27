# Intuition
My first thought is to leverage reversing the entire string and then reversing individual words to achieve the desired order. This allows us to handle extra spaces easily and ensures that words are reversed efficiently.

# Approach
1. **Reverse the Entire String**: By reversing the whole string, the order of the words is reversed, but the words themselves are also reversed.
2. **Reverse Each Word**: Iterate through the reversed string to reverse each word back to its original form.
3. **Clean Up Spaces**: Remove leading, trailing, and multiple spaces to ensure words are separated by a single space.

# Complexity
- Time complexity: $$O(n)$$, where \(n\) is the length of the string. Each character is processed a constant number of times.
- Space complexity: $$O(n)$$, for storing the cleaned-up string as a new string.

# Code
```java
public class Solution {
    public String reverseWords(String s) {
        char[] str = s.toCharArray();
        int n = str.length;

        // Step 1: Reverse the whole string
        reverse(str, 0, n - 1);

        // Step 2: Reverse each word in the reversed string
        reverseWords(str, n);

        // Step 3: Clean up spaces
        return cleanSpaces(str, n);
    }

    private void reverse(char[] str, int start, int end) {
        while (start < end) {
            char temp = str[start];
            str[start] = str[end];
            str[end] = temp;
            start++;
            end--;
        }
    }

    private void reverseWords(char[] str, int n) {
        int start = 0, end = 0;

        while (start < n) {
            while (start < end || start < n && str[start] == ' ') start++; // skip spaces
            while (end < start || end < n && str[end] != ' ') end++; // skip non spaces
            reverse(str, start, end - 1); // reverse the word
        }
    }

    private String cleanSpaces(char[] str, int n) {
        int i = 0, j = 0;

        while (j < n) {
            while (j < n && str[j] == ' ') j++; // skip spaces
            while (j < n && str[j] != ' ') str[i++] = str[j++]; // keep non spaces
            while (j < n && str[j] == ' ') j++; // skip spaces
            if (j < n) str[i++] = ' '; // keep only one space
        }

        return new String(str).substring(0, i);
    }
}
```