# Intuition
To find the number of subarrays whose sum equals k, we can leverage the concept of prefix sums. The idea is to keep track of the cumulative sum of elements up to each index and use a hashmap to store the frequency of these sums. This allows us to quickly determine if a subarray with the required sum exists.

# Approach
Initialize Variables:

count to keep track of the number of subarrays with sum k.
sum to store the cumulative sum of elements.
sumCount to store the frequency of each cumulative sum encountered.
Edge Case: Insert (0, 1) into sumCount to handle cases where a subarray starting from index 0 has a sum equal to k.

Iterate Through Array:

Add the current element to sum.
Check if (sum - k) exists in sumCount. If it does, it means there is a subarray ending at the current index which sums to k. Add the frequency of (sum - k) to count.
Update sumCount with the current sum. If sum already exists in the map, increment its frequency by 1. Otherwise, insert it with a frequency of 1.
Return count: This will be the total number of subarrays whose sum equals k.

# Complexity
Time complexity:
The time complexity is O(n), where n is the length of the input array. This is because we iterate through the array once, and each operation with the hashmap (insertion and lookup) is average O(1).

Space complexity:
The space complexity is O(n), where n is the length of the input array. This is because, in the worst case, we might store all the cumulative sums in the hashmap.

# Code

```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public int subarraySum(int[] nums, int k) {
        int count = 0;
        int sum = 0;
        Map<Integer, Integer> sumCount = new HashMap<>();
        sumCount.put(0, 1); // To handle the case when subarray starts from index 0
        
        for (int num : nums) {
            sum += num;
            
            // Check if there is a subarray (sum - k) which ends at the current index
            if (sumCount.containsKey(sum - k)) {
                count += sumCount.get(sum - k);
            }
            
            // Update the map with the current cumulative sum
            sumCount.put(sum, sumCount.getOrDefault(sum, 0) + 1);
        }
        
        return count;
    }
}
```