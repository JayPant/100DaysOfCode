

# **Intuition**
The problem can be approached by first sorting the pairs based on their second elements. This way, we can apply a greedy algorithm to find the maximum length of a chain where each pair can follow another if the first element of a pair is greater than the second element of the previous pair in the chain.

# **Approach**
1. **Sort the Pairs:**
   - Sort the pairs based on their second elements. This allows us to always choose the pair that leaves the most room for subsequent pairs.

2. **Initialize the Chain:**
   - Start with the first pair in the sorted array, and initialize the chain length and chain end to the second element of this pair.

3. **Iterate through Pairs:**
   - For each subsequent pair, check if its first element is greater than the current chain end.
   - If it is, increment the chain length and update the chain end to the second element of the current pair.

4. **Return the Result:**
   - The length of the chain is returned as the result.

# **Complexity**
- **Time Complexity:** $$O(n \log n)$$ due to the sorting step, where \(n\) is the number of pairs.
- **Space Complexity:** $$O(1)$$ as we are using only a few extra variables for tracking the chain length and chain end.

#### **Code**
```java
class Solution {
    public int findLongestChain(int[][] pairs) {
        // Step 1: Sort pairs based on their second element
        Arrays.sort(pairs, Comparator.comparingDouble(o -> o[1]));

        // Step 2: Initialize the chain length and chain end
        int chainLen = 1;
        int chainEnd = pairs[0][1];

        // Step 3: Iterate through pairs to build the chain
        for (int i = 1; i < pairs.length; i++) {
            if (pairs[i][0] > chainEnd) {
                chainLen++;
                chainEnd = pairs[i][1];
            }
        }

        // Step 4: Return the length of the longest chain
        return chainLen;
    }
}
```

