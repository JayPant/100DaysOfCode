# Intuition
To solve the problem of finding all unique quadruplets that sum to a given target, we can use a similar approach to the three-sum problem by extending it to four elements. Sorting the array helps in efficiently skipping duplicates and utilizing the two-pointer technique.

# Approach
1. **Sort the Array:** This helps in efficiently finding and skipping duplicate elements.
2. **Iterate with Nested Loops:** Use two nested loops to fix the first two elements of the quadruplet.
3. **Two-Pointer Technique:** For the remaining two elements, use the two-pointer technique to find pairs that sum to the remaining target.
4. **Avoid Duplicates:** Skip duplicate elements to ensure the solution set does not contain duplicate quadruplets.

# Complexity
- **Time complexity:**
  $$O(n^3)$$ 
  The array is sorted in \(O(n \log n)\) time, and finding quadruplets is done in \(O(n^3)\) time.

- **Space complexity:**
  $$O(1)$$ 
  No additional space is used other than the output list.

# Code
```java
class Solution {
    public List<List<Integer>> fourSum(int[] nums, int target) {
        List<List<Integer>> ans = new ArrayList<>();
        Arrays.sort(nums); // Sort the array
        int n = nums.length;

        for (int i = 0; i < n - 3; i++) {
            // Skip duplicate elements
            if (i > 0 && nums[i] == nums[i - 1]) {
                continue;
            }
            for (int j = i + 1; j < n - 2; j++) {
                // Skip duplicate elements
                if (j > i + 1 && nums[j] == nums[j - 1]) {
                    continue;
                }
                int left = j + 1;
                int right = n - 1;

                while (left < right) {
                    long sum = (long) nums[i] + nums[j] + nums[left] + nums[right];
                    if (sum == target) {
                        ans.add(Arrays.asList(nums[i], nums[j], nums[left], nums[right]));
                        // Skip duplicates for left and right pointers
                        while (left < right && nums[left] == nums[left + 1]) left++;
                        while (left < right && nums[right] == nums[right - 1]) right--;
                        left++;
                        right--;
                    } else if (sum < target) {
                        left++; // Move left pointer to the right to increase the sum
                    } else {
                        right--; // Move right pointer to the left to decrease the sum
                    }
                }
            }
        }
        return ans;
    }
}
```
