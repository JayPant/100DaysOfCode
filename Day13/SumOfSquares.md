# Intuition
To determine if there exist two integers (a) and (b) such that (a^2 + b^2 = c), the first thought is to leverage the properties of squares and use a two-pointer approach. This approach is efficient and reduces the complexity compared to checking every possible pair.

# Approach
Initialize Pointers: Start with two pointers, left initialized to 0 and right initialized to (\sqrt{c}). This is because the maximum value for (a) or (b) such that (a^2 + b^2 = c) is (\sqrt{c}).
Two-Pointer Technique:
Calculate the sum of squares of the numbers pointed to by the left and right pointers.
If the sum equals (c), return true.
If the sum is less than (c), increment the left pointer to increase the sum.
If the sum is greater than (c), decrement the right pointer to decrease the sum.
Repeat the process until left exceeds right.
Termination:
If no such pair is found and the loop terminates, return false.

# Complexity
Time complexity: (O(\sqrt{c}))
The while loop runs as long as left is less than or equal to right, and since right starts at (\sqrt{c}) and only decrements, the number of iterations is at most (\sqrt{c}).
Space complexity: (O(1))
We only use a constant amount of extra space for the left, right, and sum variables.

# Code

```java
class Solution {
    public boolean judgeSquareSum(int c) {
        long left = 0;
        long right = (long) Math.sqrt(c);
        
        while (left <= right) {
            long sum = left * left + right * right;
            if (sum == c) {
                return true;
            } else if (sum < c) {
                left++;
            } else {
                right--;
            }
        }
        
        return false;
    }
}
```