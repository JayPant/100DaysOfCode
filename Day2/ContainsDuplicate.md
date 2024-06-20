# Intuition
My first thought was to use a data structure that allows for fast lookup and insertion operations. Since we need to check for duplicates in an array, a HashSet is ideal because it can store unique elements and provides constant-time complexity for both checking the presence of an element and adding an element.

# Approach
Initialize a HashSet to keep track of the elements we have seen so far.
Iterate through each element in the array.
For each element, check if it is already present in the HashSet:
If it is, return true because we have found a duplicate.
If it is not, add the element to the HashSet.
If the loop completes without finding any duplicates, return false.

# Complexity
Time complexity:
The time complexity is (O(n)), where (n) is the number of elements in the array. This is because we perform constant-time operations (checking for the presence of an element and adding an element) for each element in the array.

Space complexity:
The space complexity is (O(n)), where (n) is the number of elements in the array. In the worst case, if all elements are unique, we will store all (n) elements in the HashSet.

# Code

```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> verify = new HashSet<>();

        for (int num : nums) {
            if (verify.contains(num)) {
                return true;
            }
            verify.add(num);
        }

        return false;
    }
}
```