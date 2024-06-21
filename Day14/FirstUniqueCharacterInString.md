# Intuition
To find the first unique character in a string, we need to determine the frequency of each character. By doing this, we can then identify the first character in the string that has a frequency of one.

# Approach
Count Frequency:

Use an array to store the frequency of each character in the string.
Traverse the string and update the frequency count for each character.
Find First Unique Character:

Traverse the string again and check the frequency count for each character.
Return the index of the first character with a frequency of one.


# Complexity

Time complexity:
The algorithm runs in (O(n)) time, where (n) is the length of the string. This is because we traverse the string twice (once to count the frequencies and once to find the first unique character).

Space complexity:
The space complexity is (O(1)) because the size of the frequency array is constant (26 letters in the English alphabet).

Code

```java
class Solution {
    public int firstUniqChar(String s) {
        int n = s.length();
        int[] count = new int[26]; // Frequency array for characters 'a' to 'z'
        char[] ch = s.toCharArray();
        
        // Count frequency of each character
        for (int i = 0; i < n; i++) {
            count[ch[i] - 'a']++;
        }
        
        // Find the first unique character
        for (int i = 0; i < n; i++) {
            if (count[ch[i] - 'a'] == 1) {
                return i;
            }
        }
        
        return -1; // No unique character found
    }
}
```