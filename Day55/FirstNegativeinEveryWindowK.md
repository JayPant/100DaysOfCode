```java

    public long[] printFirstNegativeInteger(long arr[], int N, int k)
    {
        int start = 0, end = 0;
        long[] ans = new long[N - k + 1];
        int idx = 0;
        
        List<Long> list = new ArrayList<>();
        
        while (end < N) {
            // Add current element to list if it's negative
            if (arr[end] < 0)
                list.add(arr[end]);
            
            // Determine the first negative integer for the current window
            if (end - start + 1 >= k) {
                // If list is not empty, the first element is the answer
                ans[idx++] = list.isEmpty() ? 0 : list.get(0);
                
                // Remove the first element of the list if it's out of the current window
                if (!list.isEmpty() && list.get(0).equals(arr[start]))
                    list.remove(0);
                
                // Move window ahead
                start++;
            }
            
            // Move to the next element in the array
            end++;
        }
        
        return ans;
    }
}
```