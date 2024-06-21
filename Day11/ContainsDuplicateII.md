# Intuition
To solve this problem, my first thought is to use a data structure that allows for efficient lookups to keep track of the indices of the elements we've seen so far. A HashMap will be ideal for this purpose because it allows for constant-time complexity for insertions and lookups. As we iterate through the array, we'll store each element and its index in the HashMap. If we encounter an element that's already in the HashMap, we'll check the difference between the current index and the stored index. If this difference is less than or equal to ( k ), we return true. If we complete the iteration without finding such a pair, we return false.

# Approach
Create a HashMap called valueIndexMap to store elements and their latest indices.
Iterate through the array nums using a for loop.
For each element nums[i]:
Check if nums[i] is already in the HashMap.
If it is, get the previous index of nums[i] from the HashMap.
Check if the absolute difference between the current index i and the stored index is less than or equal to ( k ).
If the condition is satisfied, return true.
If the condition is not satisfied, update the HashMap with the current index i for nums[i].
If no such pair is found after iterating through the array, return false.

# Complexity
Time complexity: ( O(n) ), where ( n ) is the number of elements in the array. This is because we make a single pass through the array and each insertion and lookup operation in the HashMap is ( O(1) ).
Space complexity: ( O(n) ) in the worst case, where ( n ) is the number of elements in the array. This is because in the worst case, we might store all elements in the HashMap.

# Code

```java
class Solution {
    public boolean containsNearbyDuplicate(int[] nums, int k) {
        HashMap<Integer, Integer> valueIndexMap = new HashMap<>();

        for (int i = 0; i < nums.length; i++) {
            // Check if the value already exists in the HashMap
            if (valueIndexMap.containsKey(nums[i])) {
                // Get the previous index of this value
                int j = valueIndexMap.get(nums[i]);
                // Check the condition
                if (Math.abs(i - j) <= k) {
                    return true; // Exit the program as we found a valid pair
                }
            }

            // Update the HashMap with the current index of the value
            valueIndexMap.put(nums[i], i);
        }
        return false;
    }
}
```





















