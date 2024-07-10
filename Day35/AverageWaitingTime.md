
## Intuition
The problem requires calculating the average waiting time for a series of customers, where each customer has a specific arrival time and a time required to prepare their order. The idea is to simulate the process of serving the customers in the order they arrive and compute the waiting time for each customer.

## Approach
1. **Initialization**: Start by initializing the total waiting time with the waiting time of the first customer. Also, keep track of the finish time of the previous customer.

2. **Iterate through Customers**: For each subsequent customer:
   - Determine the start time for preparing the current customer's order. This is either their arrival time or the time when the previous order finished, whichever is later.
   - Calculate the time when the current customer's order will be finished.
   - Update the total waiting time by adding the waiting time for the current customer, which is the difference between their order finish time and their arrival time.
   - Update the finish time of the previous customer to the current customer's finish time.

3. **Calculate Average**: Finally, compute the average waiting time by dividing the total waiting time by the number of customers.

## Complexity

### Time Complexity
The algorithm iterates through each customer exactly once, performing a constant amount of work for each customer. Thus, the time complexity is:
$$O(n)$$
where \(n\) is the number of customers.

### Space Complexity
The algorithm uses a constant amount of extra space for variables such as `waitingTime`, `prevFinish`, `start`, and `takewaytime`. Thus, the space complexity is:
$$O(1)$$

## Code
```java
class Solution {
    public double averageWaitingTime(int[][] customers) {
        double waitingTime = customers[0][1];
        int prevFinish = customers[0][0] + customers[0][1];

        for (int i = 1; i < customers.length; i++) {
            int[] time = customers[i];
            int arvtime = time[0];

            int start = Math.max(arvtime, prevFinish);
            int takewaytime = start + time[1];

            prevFinish = takewaytime;
            waitingTime += takewaytime - arvtime; 
        }

        return waitingTime / customers.length;
    }
}
```
