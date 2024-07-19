
# Intuition
The span of the stock's price today is defined as the maximum number of consecutive days (starting from today and going backward) for which the price of the stock was less than or equal to today's price. This can be efficiently solved using a stack to keep track of previous prices and their spans.

# Approach
1. Use two stacks:
   - `prices`: to keep track of the stock prices.
   - `spans`: to keep track of the spans of each price in the `prices` stack.
2. For each new price:
   - Initialize the current span to 1 (at least today counts).
   - While the stack is not empty and the top of the `prices` stack is less than or equal to the current price:
     - Pop the top of both stacks and add the span from the `spans` stack to the current span.
   - Push the current price and its span onto their respective stacks.
3. Return the current span.

# Complexity
- **Time complexity:**  
    $$O(n)$$ where \(n\) is the number of prices processed. Each price is pushed and popped from the stack at most once.
- **Space complexity:**  
    $$O(n)$$ for the stacks storing the prices and spans.

# Code
```java
import java.util.Stack;

class StockSpanner {
    private Stack<Integer> prices;
    private Stack<Integer> spans;

    public StockSpanner() {
        prices = new Stack<>();
        spans = new Stack<>();
    }
    
    public int next(int price) {
        int span = 1;
        
        while (!prices.isEmpty() && prices.peek() <= price) {
            prices.pop();
            span += spans.pop();
        }
        
        prices.push(price);
        spans.push(span);
        
        return span;
    }
}
```

<details>
<summary>Python</summary>

```python
class StockSpanner:

    def __init__(self):
        self.prices = []
        self.spans = []

    def next(self, price: int) -> int:
        span = 1
        while self.prices and self.prices[-1] <= price:
            self.prices.pop()
            span += self.spans.pop()
        self.prices.append(price)
        self.spans.append(span)
        return span
```
</details>

<details>
<summary>C++</summary>

```cpp
#include <stack>
using namespace std;

class StockSpanner {
    stack<int> prices, spans;
public:
    StockSpanner() {}

    int next(int price) {
        int span = 1;
        while (!prices.empty() && prices.top() <= price) {
            prices.pop();
            span += spans.top();
            spans.pop();
        }
        prices.push(price);
        spans.push(span);
        return span;
    }
};
```
</details>

