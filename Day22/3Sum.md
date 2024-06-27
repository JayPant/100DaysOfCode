# Intuition
My first thought is to use a method that avoids redundant operations and handles duplicates efficiently. Sorting the array will help in systematically finding triplets that sum to zero using a two-pointer technique.

# Approach
1. **Sort the Array:** Sorting helps in efficiently finding and skipping duplicates.
2. **Iterate Through the Array:** Treat each element as the first element of the triplet.
3. **Two-Pointer Technique:** Use two pointers, starting just after the current element and from the end of the array, to find pairs that sum up to the negative of the current element.
4. **Avoid Duplicates:** Skip duplicate elements to ensure the solution set does not contain duplicate triplets.

# Complexity
- **Time complexity:** 
  $$O(n^2)$$ 
  The array is sorted in \(O(n \log n)\) time, and finding triplets is done in \(O(n^2)\) time.
  
- **Space complexity:** 
  $$O(1)$$ 
  No additional space is used other than the output list.

# Code
```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        Arrays.sort(nums); // Sort the array

        for (int i = 0; i < nums.length - 2; i++) {
            // Skip duplicate elements
            if (i > 0 && nums[i] == nums[i - 1]) {
                continue;
            }

            int left = i + 1;
            int right = nums.length - 1;

            // Use two-pointer technique to find pairs that sum to the negative of nums[i]
            while (left < right) {
                int sum = nums[i] + nums[left] + nums[right];
                if (sum == 0) {
                    ans.add(Arrays.asList(nums[i], nums[left], nums[right]));
                    // Skip duplicates for left and right pointers
                    while (left < right && nums[left] == nums[left + 1]) left++;
                    while (left < right && nums[right] == nums[right - 1]) right--;
                    left++;
                    right--;
                } else if (sum < 0) {
                    left++; // Move left pointer to the right to increase the sum
                } else {
                    right--; // Move right pointer to the left to decrease the sum
                }
            }
        }
        return ans;
    }
}
```
