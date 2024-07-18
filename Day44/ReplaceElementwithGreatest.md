
# Intuition
The goal is to replace each element in the array with the greatest element among the elements to its right, and replace the last element with -1. We need to traverse the array from right to left to keep track of the maximum element seen so far.

# Approach
1. Initialize `max` to -1 (as the last element should be replaced by -1).
2. Traverse the array from the end to the beginning.
3. For each element, store its value in a temporary variable.
4. Replace the current element with the value of `max`.
5. Update `max` to be the maximum of its current value and the stored value of the current element.
6. Continue this process until all elements are replaced appropriately.

# Complexity
- **Time complexity:**  
    $$O(n)$$ where \(n\) is the length of the array. We traverse the array once.

- **Space complexity:**  
    $$O(1)$$ since we are using only a constant amount of extra space.

# Code

```java
class Solution {
    public int[] replaceElements(int[] arr) {
        int n = arr.length;
        int max = -1;
        
        for (int i = n - 1; i >= 0; i--) {
            int current = arr[i];
            arr[i] = max;
            max = Math.max(max, current);
        }
        
        return arr;
    }
}
```

<details>
<summary>Python</summary>

```python
class Solution:
    def replaceElements(self, arr: List[int]) -> List[int]:
        n = len(arr)
        max_val = -1
        
        for i in range(n - 1, -1, -1):
            current = arr[i]
            arr[i] = max_val
            max_val = max(max_val, current)
        
        return arr
```
</details>

<details>
<summary>C++</summary>

```cpp
class Solution {
public:
    vector<int> replaceElements(vector<int>& arr) {
        int n = arr.size();
        int max_val = -1;
        
        for (int i = n - 1; i >= 0; i--) {
            int current = arr[i];
            arr[i] = max_val;
            max_val = max(max_val, current);
        }
        
        return arr;
    }
};
```
</details>
