
# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
To determine if one string is a rotation of another, the primary idea is to recognize that if we concatenate the goal string with itself, it will contain all possible rotations of the goal string as substrings. Thus, we can simply check if the original string `s` is a substring of this concatenated string.

# Approach
<!-- Describe your approach to solving the problem. -->
1. **Edge Case Handling:** Check if either string is `null` or if their lengths do not match. If so, return `false`.
2. **Concatenation:** Concatenate the `goal` string with itself.
3. **Substring Check:** Use the `contains` method to check if the original string `s` is a substring of the concatenated string `goal + goal`.
4. **Return Result:** If `s` is found as a substring, return `true`; otherwise, return `false`.

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
The time complexity is $$O(n)$$ where n is the length of the string. The `contains` method internally uses an efficient substring search algorithm, which runs in linear time.

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
The space complexity is $$O(n)$$ due to the space required to store the concatenated string `goal + goal`.

# Code
```java
class Solution {
    public boolean rotateString(String s, String goal) {
        if (s == null || goal == null || s.length() != goal.length()) {
            return false;
        }

        String match = goal + goal;
        return match.contains(s);
    }
}
```
