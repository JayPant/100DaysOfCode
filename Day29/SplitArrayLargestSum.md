
# Intuition
The problem requires us to split an array into m subarrays such that the maximum sum of any subarray is minimized. To achieve this, we need to efficiently determine the minimum possible value of this maximum sum.

# Approach
1. **Initial Setup**: Calculate the total sum of the array (`sum`) and find the maximum element (`max`) in the array. These values will help in setting up the binary search range.
  
2. **Binary Search**: Use binary search to efficiently find the minimum possible maximum sum (`mid`). The search range is initialized from `max` (since each subarray must contain at least one element equal to `max`) to `sum` (the total sum of all elements).

3. **Partition Counting**: For each mid value (potential maximum sum of subarray):
   - Implement `countPartition` function to count how many partitions (subarrays) are needed if the maximum sum of any subarray is `mid`.
   - Iterate through the array, adding elements to the current partition until adding another element would exceed `mid`. When it does, increment the partition count and start a new partition.

4. **Adjust Search Range**: Adjust the binary search based on the number of partitions:
   - If the number of partitions (`partition`) exceeds `m`, it means `mid` is too small, so adjust `low` to `mid + 1`.
   - If the number of partitions is `m` or less, `mid` is a potential solution, so adjust `high` to `mid - 1` to find a smaller possible maximum sum.

5. **Return Result**: The smallest `low` value after the binary search concludes will be the minimum possible maximum sum that allows the array to be split into `m` subarrays.

# Complexity
- **Time complexity**: `O(nlog(sum−max))`, where \( n \) is the length of the array. 
  
- **Space complexity**: `O(1)` - The additional space used is constant, apart from the input array.

# Code
```java
import java.util.Arrays;
class Solution {

 static int countPartition(int[] nums, int maxSum) {
        int countPart = 1;
        int elementSum = 0;

        for (int i = 0; i < nums.length; i++) {
            if (elementSum + nums[i] > maxSum) {
                countPart++;
                elementSum = nums[i];
            } else {
                elementSum += nums[i];
            }
        }
        return countPart;
    }

    public int splitArray(int[] nums, int m) {
        if(m>nums.length) return -1; 
        
        int sum=0, max = Integer.MIN_VALUE;
         for (int num : nums) {
            sum += num;
            max = Math.max(max, num);
        }
        int low =max;
        int high = sum;

        while (low <= high) {
            int mid = low + (high - low) / 2;
            int partition = countPartition(nums, mid);

            if (partition > m) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
        return low;
    }
}
```