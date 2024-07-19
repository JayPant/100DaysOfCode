
# Intuition
The problem is to determine if a given string of brackets is valid. A valid string of brackets means every opening bracket has a corresponding closing bracket in the correct order. Our first thought is to use a stack to help manage the opening and closing brackets.

# Approach
1. Use a stack to keep track of the opening brackets.
2. Traverse through the string:
   - If the character is an opening bracket (`(`, `{`, `[`), push it onto the stack.
   - If the character is a closing bracket (`)`, `}`, `]`), check if the stack is not empty and if the top of the stack is the corresponding opening bracket. If it is, pop the stack. Otherwise, return false.
3. After traversing the string, if the stack is empty, all brackets were matched correctly, so return true. Otherwise, return false.

# Complexity
- **Time complexity:**  
    $$O(n)$$ where \(n\) is the length of the input string. We traverse the string once.

- **Space complexity:**  
    $$O(n)$$ in the worst case, where \(n\) is the number of characters in the input string. This occurs when all characters are opening brackets and get pushed onto the stack.

# Code
```java
import java.util.Stack;

class Solution {
    public boolean isValid(String str) {
        Stack<Character> s = new Stack<>();
        for (int i = 0; i < str.length(); i++) {
            char ch = str.charAt(i);

            if (ch == '(' || ch == '{' || ch == '[') {
                s.push(ch);
            } else {
                if (s.isEmpty()) {
                    return false;
                }
                if (s.peek() == '(' && ch == ')' 
                    || s.peek() == '{' && ch == '}' 
                    || s.peek() == '[' && ch == ']') {
                    s.pop();
                } else {
                    return false;
                }
            }
        }
        return s.isEmpty();
    }
}
```

<details>
<summary>Python</summary>

```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        mapping = {")": "(", "}": "{", "]": "["}

        for char in s:
            if char in mapping:
                top_element = stack.pop() if stack else '#'
                if mapping[char] != top_element:
                    return False
            else:
                stack.append(char)

        return not stack
```
</details>

<details>
<summary>C++</summary>

```cpp
#include <stack>
#include <unordered_map>

class Solution {
public:
    bool isValid(std::string s) {
        std::stack<char> stack;
        std::unordered_map<char, char> mapping = {
            {')', '('},
            {'}', '{'},
            {']', '['}
        };

        for (char c : s) {
            if (mapping.find(c) != mapping.end()) {
                char top_element = stack.empty() ? '#' : stack.top();
                stack.pop();
                if (top_element != mapping[c]) {
                    return false;
                }
            } else {
                stack.push(c);
            }
        }

        return stack.empty();
    }
};
```
</details>

