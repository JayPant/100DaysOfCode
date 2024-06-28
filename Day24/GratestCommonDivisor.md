# Intuition
To solve this problem, we need to find the GCD of the smallest and largest numbers in the given array. The GCD of two numbers is the largest number that divides both of them without leaving a remainder. 

# Approach
1. **Find the Minimum and Maximum Elements**: 
   - Iterate through the array to find the minimum and maximum elements.
2. **Calculate the GCD**: 
   - Use the Euclidean algorithm to compute the GCD of the minimum and maximum elements. The Euclidean algorithm involves repeatedly replacing the larger number by its remainder when divided by the smaller number until one of the numbers becomes zero. The non-zero number at this point is the GCD.

# Complexity
- **Time complexity**:
  - Finding the minimum and maximum elements each takes \(O(n)\), where \(n\) is the number of elements in the array.
  - The Euclidean algorithm for GCD takes \(O(\log(\min(a, b)))\), where \(a\) and \(b\) are the two numbers.
  - Overall, the time complexity is \(O(n + \log(\min(a, b)))\), which simplifies to \(O(n)\) because \(n\) dominates \(\log(\min(a, b))\).

- **Space complexity**:
  - The space complexity is \(O(1)\) as we are using a constant amount of extra space regardless of the input size.

# Code
```java
class Solution {

    private int gcd(int max, int min) {
        while (min != 0) {
            int temp = min;
            min = max % min;
            max = temp;
        }
        return max;
    }

    public int findGCD(int[] nums) {
        int min = findMin(nums);
        int max = findMax(nums);

        return gcd(max, min);
    }

    private int findMin(int[] nums) {
        int min = Integer.MAX_VALUE;
        for (int num : nums) {
            if (num < min) {
                min = num;
            }
        }
        return min;
    }

    private int findMax(int[] nums) {
        int max = Integer.MIN_VALUE;
        for (int num : nums) {
            if (num > max) {
                max = num;
            }
        }
        return max;
    }
}
```
