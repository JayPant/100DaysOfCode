# Intuition
The intuition behind this problem is to use bitwise operations to perform addition. The XOR operation can be used to add bits where there is no carry, and the AND operation followed by a left shift can be used to calculate the carry.

# Approach
1. **Initialize Variables**: Set `ans` to store the result of the XOR operation and `carry` to store the result of the AND operation followed by a left shift.
2. **Bitwise XOR and AND Operations**: Perform the XOR operation between `a` and `b` to simulate addition without carry and store the result in `ans`. Perform the AND operation between `a` and `b`, left shift the result by 1 to calculate the carry, and store it in `carry`.
3. **Update `a` and `b`**: Set `a` to `ans` and `b` to `carry`.
4. **Repeat Until No Carry**: Continue the process until `b` becomes 0, meaning there is no carry left to add.

# Complexity
- **Time Complexity**: The time complexity is \(O(\log(\text{max}(a, b)))\) because the number of operations depends on the number of bits in the maximum of `a` and `b`.
- **Space Complexity**: The space complexity is \(O(1)\) since only a fixed amount of extra space is used.

# Code
```java
class Solution {
    public int getSum(int a, int b) {
        int ans = 0;
        int carry = 0;

        while (b != 0) {
            ans = a ^ b; // Add without carry
            carry = a & b; // Calculate carry
            carry = carry << 1; // Shift carry to the left
            a = ans; // Update a with the new value
            b = carry; // Update b with the new carry
        }

        return a; // a contains the result
    }
}
```

