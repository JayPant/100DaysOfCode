# Intuition
To find the longest consecutive sequence in an array, we need to determine the length of the longest sequence of consecutive integers. This can be efficiently achieved using a set to check for the existence of elements.

# Approach
Initialization and Edge Case Handling:

If the input array nums is empty, return 0 immediately.
Populate the Set:

Create a set set and add all elements from nums to it. This ensures O(1) lookup time for each element.
Find the Longest Consecutive Sequence:

Iterate through each element in the set.
For each element, check if it is the start of a sequence by checking if i - 1 is not in the set.
If it is the start of a sequence, count the length of the sequence by checking the presence of subsequent elements.
Update the longest variable if the current sequence is longer than the previously recorded longest sequence.
Return the Result:

After iterating through all elements, return the longest consecutive sequence length.

# Complexity
Time complexity:

Adding all elements to the set takes (O(n)) time.
Iterating through the set and counting the length of sequences also takes (O(n)) time, since each element is processed at most twice.
Thus, the overall time complexity is (O(n)).
Space complexity:

The space complexity is (O(n)) due to the additional set used to store the elements.

# Code

```java
class Solution {
    public int longestConsecutive(int[] nums) {
        if (nums.length == 0) return 0;

        Set<Integer> set = new HashSet<>();

        for (int num : nums) {
            set.add(num);
        }
          
        int longest = 1;

        for (int i : set) {
            if (!set.contains(i - 1)) {
                int count = 1;
                int next = i;

                while (set.contains(next + 1)) {
                    next++;
                    count++;
                }
                longest = Math.max(longest, count);
            }
        }

        return longest;
    }
}
```