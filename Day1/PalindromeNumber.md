# Intuition
To determine if a number is a palindrome, we need to check if it reads the same backward as forward. My first thought is to reverse the digits of the number and compare it with the original number.

# Approach
Store the original number in a temporary variable.
Initialize variables to store the remainder of each digit and the reversed number.
Use a loop to reverse the digits of the number:
Extract the last digit of the temporary variable using modulo operation.
Add this digit to the reversed number.
Remove the last digit from the temporary variable by dividing it by 10.
Compare the reversed number with the original number.
If they are equal and the number is non-negative, return true. Otherwise, return false.
Complexity
Time complexity:
The time complexity is (O(\log_{10} n)) because we are processing each digit of the number, and the number of digits is proportional to (\log_{10} n).

# Space complexity:
The space complexity is (O(1)) as we are using a constant amount of extra space.

# Code

```java
class Solution {
    public boolean isPalindrome(int x) {
        int temp = x;
        int rem = 0;
        int num = 0;

        while (temp != 0) {
            rem = temp % 10;
            num = num * 10 + rem;
            temp = temp / 10;
        }

        if (num == x && num >= 0) return true;
        
        return false;
    }
}
```