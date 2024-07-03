
### Explanation:

1. **countStudent Method**:
   - This method `countStudent` calculates how many students are required if each student can read up to `pages` number of pages.
   - It iterates through the list `arr` (which contains the number of pages in each book) and keeps track of the `pageCount` for the current student.
   - If adding the pages of the current book to `pageCount` exceeds `pages`, it increments the `student` count and resets `pageCount` to the pages of the current book.
   - Returns the total number of students required.

2. **findPages Method**:
   - This method `findPages` is the main function that uses binary search to find the minimum possible maximum number of pages that can be assigned to any student (`mid`).
   - It first checks if there are fewer books than students (`m`). If so, it's impossible to allocate books as required, so it returns `-1`.
   - It initializes `sum` as the total number of pages in all books and `max` as the maximum number of pages in any single book.
   - Uses binary search with `low` starting from `max` and `high` starting from `sum` to find the optimal `mid`.
   - In each iteration of binary search, it calls `countStudent` to determine how many students are needed if the maximum pages per student is `mid`.
   - Adjusts `low` and `high` based on whether the number of students (`countStd`) required is greater than `m`.

3. **Complexity**:
   - **Time Complexity**: O(nlog(sum)), where n is the number of books (size of `arr`). This complexity arises from the binary search (`log(sum)`) and the linear scan in `countStudent` (`O(n)`).
   - **Space Complexity**: O(1), as the additional space used is constant, apart from the input list `arr`.

### Code:
```java
import java.util.ArrayList;

public class Solution {
    private static int countStudent(ArrayList<Integer> arr, int pages) {
        int student = 1;
        int pageCount = 0;

        for (int i = 0; i < arr.size(); i++) {
            if (pageCount + arr.get(i) <= pages) {
                pageCount += arr.get(i);
            } else {
                student++;
                pageCount = arr.get(i);
            }
        }
        return student;
    }
    
    public static int findPages(ArrayList<Integer> arr, int n, int m) {
        if (arr.size() < m) {
            return -1; // More students than books
        }
        int sum = 0, max = Integer.MIN_VALUE;
        for (int num : arr) {
            sum += num;
            max = Math.max(max, num);
        }
        int low = max;
        int high = sum;

        while (low <= high) {
            int mid = low + (high - low) / 2;
            int countStd = countStudent(arr, mid);

            if (countStd > m) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }

        return low;
    }
}
```
