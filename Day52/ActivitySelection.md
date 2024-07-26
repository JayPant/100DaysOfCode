
#### **Intuition**
The key insight is to always pick the activity that ends the earliest. This way, we maximize the remaining time for other activities.

#### **Approach**
1. **Create a List of Activities:**
   - Pair each start time with its corresponding end time.

2. **Sort Activities:**
   - Sort the list of activities based on their end times. This allows us to always choose the activity that finishes the earliest.

3. **Select Activities:**
   - Initialize the count of maximum activities.
   - Keep track of the end time of the last selected activity.
   - Iterate through the sorted activities, and for each activity, if its start time is greater than the end time of the last selected activity, select this activity.

4. **Return the Result:**
   - The total number of selected activities is returned.

#### **Complexity**
- **Time Complexity:** $$O(n \log n)$$ due to the sorting step, where \(n\) is the number of activities.
- **Space Complexity:** $$O(n)$$ for storing the start and end times in a new array of pairs.

#### **Code**
```java
import java.util.Arrays;
import java.util.Comparator;

class Solution {
    // Function to find the maximum number of activities that can
    // be performed by a single person.
    public static int activitySelection(int start[], int end[], int n) {
        // Create an array of activities, each activity represented as [start, end]
        int[][] activities = new int[n][2];
        
        for (int i = 0; i < n; i++) {
            activities[i][0] = start[i];
            activities[i][1] = end[i];
        }
        
        // Sort activities based on their end times
        Arrays.sort(activities, Comparator.comparingInt(o -> o[1]));
        
        // Initialize the count of maximum activities
        int maxAct = 1;
        int lastEnd = activities[0][1];
        
        // Iterate through the sorted activities
        for (int i = 1; i < n; i++) {
            // If the start time of the current activity is greater than
            // the end time of the last selected activity, select this activity
            if (activities[i][0] > lastEnd) {
                maxAct++;
                lastEnd = activities[i][1];
            }
        }
        
        return maxAct;
    }
}
```

