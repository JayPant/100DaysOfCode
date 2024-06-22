# Intuition
The idea is to perform a modified binary search. We divide the array into two parts and check which part is sorted. If the left part is sorted and the target lies within the range of the left part, we continue searching in the left part, otherwise, we search in the right part. If the right part is sorted and the target lies within the range of the right part, we continue searching in the right part, otherwise, we search in the left part. We repeat this process until we find the target or the array is exhausted.

# Approach
1. Initialize `low` to 0 and `high` to `arr.length - 1`.
2. While `low` is less than or equal to `high`:
   - Calculate `mid` as `low + (high - low) / 2`.
   - If `arr[mid]` is equal to the `target`, return `mid`.
   - Check if the left part is sorted (`arr[low] <= arr[mid]`):
     - If `arr[low] <= target <= arr[mid]`, update `high` to `mid - 1` (search in the left part).
     - Otherwise, update `low` to `mid + 1` (search in the right part).
   - If the right part is sorted:
     - If `arr[mid] <= target <= arr[high]`, update `low` to `mid + 1` (search in the right part).
     - Otherwise, update `high` to `mid - 1` (search in the left part).
3. If the target is not found, return -1.

# Complexity
- Time complexity: O(log n) - Each step of the binary search reduces the search space by half.
- Space complexity: O(1) - Only a constant amount of extra space is required for variables `low`, `high`, `mid`, and the target comparison.

# Code
``` java
class Solution {
    public int search(int[] arr, int target) {
        int low = 0;
        int high = arr.length-1;

        while(low<=high)
        {
            int mid = low + (high-low) / 2;

            if(arr[mid] == target)
            {
                return mid;  //if found return it
            }

            //check for the sorted part
            if(arr[low] <= arr[mid])           
            {   
                //if low is smaller than mid means left part is sorted otherwise right part is sorted
                if(arr[low] <=target && target <= arr[mid]){
                 high=mid-1; //if  low<=target<=mid means it is in left part so eliminate right part 
                }
                else{
                    low = mid+1; //if not then eliminate left part;
                }
            }else{
                if(arr[mid] <= target && target <= arr[high])
                {
                    low = mid+1; //if  mid<=target<=high means it is in right part so eliminate left part 
                }else{
                    high=mid-1; //if not then eliminate right part;
                }
            }
        }

        return -1;

    }
}
```