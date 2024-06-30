# Intuition
The first thought is to use hash sets to find the intersection of two arrays efficiently. By leveraging the properties of sets, we can quickly check for the presence of elements and eliminate duplicates.

# Approach
1. **Use HashSets**: Create two hash sets, `set1` for storing elements from `nums1` and `set2` for storing the intersection of elements that are present in both `nums1` and `nums2`.
2. **Populate `set1`**: Add all elements from `nums1` to `set1`.
3. **Find Intersection**: Iterate through `nums2`, and if an element is present in `set1`, add it to `set2`.
4. **Convert to Array**: Convert `set2` to an array and return it as the result.

# Complexity
- **Time complexity**: 
  - The time complexity is \(O(n + m)\), where \(n\) is the length of `nums1` and \(m\) is the length of `nums2`. This is because adding elements to a set and checking for their presence are both \(O(1)\) operations on average.
  
- **Space complexity**: 
  - The space complexity is \(O(n + m)\), where \(n\) is the number of elements in `nums1` and \(m\) is the number of unique elements in the intersection. This accounts for the space needed to store the elements in the hash sets.

# Code
```java
import java.util.HashSet;

class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        HashSet<Integer> set1 = new HashSet<>();
        HashSet<Integer> set2 = new HashSet<>();
        
        // Add all elements from nums1 to set1
        for (int num : nums1) {
            set1.add(num);
        }
        
        // Add elements from nums2 to set2 if they are in set1
        for (int num : nums2) {
            if (set1.contains(num)) {
                set2.add(num);
            }
        }
        
        // Convert set2 to an array
        int[] result = new int[set2.size()];
        int i = 0;
        for (int num : set2) {
            result[i++] = num;
        }
        
        return result;
    }
}
```