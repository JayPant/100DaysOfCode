# Intuition
We will use mathematical logic to recognize a number that is divisible by 2. Specifically, if a number can be repeatedly divided by 2 until it becomes 1, then it is a power of two.

# Approach
If the number is 1, return true since (2^0 = 1).
If the number is less than 1, return false as powers of two are positive.
Use a loop to repeatedly divide the number by 2.
If at any point the number is not divisible by 2, return false.
If the number becomes 1 after repeated division, return true.

# Complexity
Time complexity:
The time complexity is (O(\log n)) because we are repeatedly dividing the number by 2, and it takes (\log n) steps to reduce the number to 1.

Space complexity:
The space complexity is (O(1)) as we are using a constant amount of extra space regardless of the input size.

# Code:

```java
class Solution {
    public boolean isPowerOfTwo(int n) {
        if (n == 1) {
            return true;
        } else if (n < 1) {
            return false;
        }

        while (n % 2 == 0) {
            n = n / 2;
        }

        return n == 1;
    }
}
```