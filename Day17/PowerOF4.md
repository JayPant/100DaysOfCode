# Intuition
To determine if a number is a power of four, we need to check two conditions:

The number should be a power of two, i.e., it should have exactly one bit set in its binary representation.
The single set bit should be in an even position (0, 2, 4, etc.), which is characteristic of powers of four.

# Approach
Check if the number is positive: Only positive numbers can be powers of four.
Check if the number is a power of two: This can be done using the bitwise operation n & (n - 1). If this operation results in 0, then n is a power of two.
Check if the set bit is in the correct position: Use a bitmask to ensure that the bit is in one of the positions that correspond to powers of four. The bitmask 0x55555555 in hexadecimal (or 01010101010101010101010101010101 in binary) ensures that the set bit is in the correct position.


# Complexity
Time complexity: O(1)O(1)O(1)

The operations performed (checking positivity, bitwise AND, and bitwise AND with a mask) are all constant time operations.
Space complexity: O(1)O(1)O(1)

The solution uses a constant amount of space for the bitmask and a few variables.

# Code

```java
class Solution {
    public boolean isPowerOfFour(int n) {
        // First, check if n is positive
        if (n <= 0) {
            return false;
        }

        // Check if n is a power of two
        if ((n & (n - 1)) != 0) {
            return false;
        }

        // Check if the only set bit is in the correct position for a power of four
        // The bitmask for positions 0, 2, 4, 6, ... is 0x55555555
        return (n & 0x55555555) != 0;
    }
}
```
