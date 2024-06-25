
# Intuition
The problem is to find the longest common prefix among an array of strings. The prefix must be common to all strings in the array. A simple way to solve this problem is to compare characters of the strings one by one.

# Approach
1. **Initial Check**: If the input array is empty, return an empty string.
2. **Set Prefix**: Use the first string in the array as the initial prefix.
3. **Iterate and Compare**: For each subsequent string, check if the current prefix is a prefix of that string. If not, shorten the prefix by one character and check again. Repeat until the prefix is found in the string or the prefix becomes an empty string.
4. **Return Prefix**: Once all strings have been checked, return the resulting prefix.

# Complexity
- **Time complexity**: $$O(S)$$, where \( S \) is the sum of all characters in all strings. In the worst case, we may need to compare all characters of each string with the prefix.
- **Space complexity**: $$O(1)$$, since we only use a constant amount of extra space to store the prefix.

# Code
```java
public class Solution {
    public String longestCommonPrefix(String[] strs) {
        // Check for empty input
        if (strs == null || strs.length == 0) return "";
        
        // Initialize the prefix with the first string
        String prefix = strs[0];
        
        // Iterate over the rest of the strings
        for (int i = 1; i < strs.length; i++) {
            // Reduce the prefix until it's a prefix of strs[i]
            while (strs[i].indexOf(prefix) != 0) {
                prefix = prefix.substring(0, prefix.length() - 1);
                if (prefix.isEmpty()) return "";
            }
        }
        
        // Return the longest common prefix
        return prefix;
    }
}
```

