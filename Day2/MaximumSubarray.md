# Intuition
This code follows basic approach of kadane's algorithm we will have two variable one for storing current sum and other for tracking the maximum sum and update both with each iteration.

# Approach
We will start having two variable:

current_sum:- For storing current sum.
max_sumL:- To track maximum sum.
According to Kadane's Algorithm we don't lept the negative values so if the current_sum is smaller than 0 i.e. neagtivr number thrn current_sum will be 0.

And then we start iterating through values and updating the max_sum.

# Complexity
Let's analyze the time and space complexity of the code:

Time Complexity
The time complexity of the code is determined by the for loop, which iterates through the entire array once.

The loop runs n times, where n is the length of the input array nums.
Each iteration of the loop performs a constant amount of work (a few arithmetic operations and comparisons).
Therefore, the time complexity is: [ O(n) ]

Space Complexity
The space complexity of the code is determined by the amount of extra space used by the algorithm, excluding the input array.

The algorithm uses a fixed amount of extra space: two integer variables (max_sum and current_sum).
Therefore, the space complexity is: [ O(1) ]

# Summary
Time Complexity: ( O(n) )
Space Complexity: ( O(1) )
It means that the algorithm is efficient in terms of both time and space, as it processes the input array in linear time and uses only a constant amount of extra space.

# Code

```java
class Solution {
    public int maxSubArray(int[] nums) {
    int max_sum = Integer.MIN_VALUE;
    int current_sum=0;

    for(int i=0;i<nums.length;i++)
    {
        current_sum+=nums[i];

        if(current_sum>max_sum) max_sum=current_sum;

        if(current_sum<0) current_sum=0;
    }

    return max_sum;
    }
}
```