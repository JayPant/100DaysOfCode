# Intuition

To find the Hamming weight (or the number of '1' bits) in the binary representation of an integer, the straightforward approach is to repeatedly check the least significant bit (LSB) and shift the integer to the right until all bits have been processed.


# Approach

Initialize a counter: Start with a counter set to 0.
Iterate through the bits of the integer:
Use a loop that continues as long as the integer is not zero.
In each iteration, use a bitwise AND operation with 1 to check the LSB. If it's 1, increment the counter.
Right shift the integer by 1 to process the next bit.
Return the counter: After processing all bits, the counter will hold the number of '1' bits in the integer.


# Complexity

Time complexity: O(log⁡n)
The number of iterations in the loop is proportional to the number of bits in the integer. For an integer ( n ), this is (log_2(n)). For a fixed-width integer (e.g., 32-bit), this simplifies to a constant (O(1)), but theoretically, it's (O(log n)).

Space complexity: O(1)
The space used by the counter and a few variables is constant.


# Code

```java
class Solution {
    public int hammingWeight(int n) {
        int count = 0;

        // Loop to count the number of '1' bits
        while (n != 0) {
            if ((n & 1) != 0) {
                count++;
            }
            n = n >>> 1; // Unsigned right shift
        }

        return count;
    }
}
```