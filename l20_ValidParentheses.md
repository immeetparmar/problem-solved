# 20. Valid Parentheses

**LeetCode Problem:** [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)

## Approach

The approach to solving the "Valid Parentheses" problem involves using a stack data structure to keep track of the opening parentheses encountered in the input string. The algorithm iterates through the string, pushing opening parentheses onto the stack and popping them off when a matching closing parenthesis is found.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Initialize an empty stack to store the opening parentheses.
2. **Step 2**: Iterate through each character in the input string.
3. **Step 3**: If the character is an opening parenthesis, push it onto the stack.
4. **Step 4**: If the character is a closing parenthesis, check if the stack is empty. If it is, return false as there's no matching opening parenthesis.
5. **Step 5**: If the stack is not empty, peek at the top element and check if it matches the current closing parenthesis. If it does, pop the top element off the stack. If it doesn't, return false.
6. **Step 6**: After iterating through the entire string, check if the stack is empty. If it is, return true as all parentheses were matched correctly. If it's not empty, return false as there are unmatched opening parentheses.

- **Time Complexity**: The time complexity of this algorithm is O(n), where n is the length of the input string, as we're iterating through the string once.
- **Space Complexity**: The space complexity is O(n) as well, as in the worst-case scenario, we might need to push all characters onto the stack.

## Dry Run

Let's take the input string `s = "({[]})"` as an example. Here's the step-by-step execution:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `st = []`, `s = "({[]})"` | Initialize stack and start iterating through string | `st = []`, `s = "({[]})"` |
| 2 | `st = []`, `s = "({[]})"` | Push '(' onto stack | `st = ['(']`, `s = "({[]})"` |
| 3 | `st = ['(']`, `s = "({[]})"` | Push '{' onto stack | `st = ['(', '{']`, `s = "({[]})"` |
| 4 | `st = ['(', '{']`, `s = "({[]})"` | Push '[' onto stack | `st = ['(', '{', '[']`, `s = "({[]})"` |
| 5 | `st = ['(', '{', '[']`, `s = "({[]})"` | Pop '[' off stack (matched with ']') | `st = ['(', '{']`, `s = "({[]})"` |
| 6 | `st = ['(', '{']`, `s = "({[]})"` | Pop '{' off stack (matched with '}') | `st = ['(']`, `s = "({[]})"` |
| 7 | `st = ['(']`, `s = "({[]})"` | Pop '(' off stack (matched with ')') | `st = []`, `s = "({[]})"` |
| 8 | `st = []`, `s = "({[]})"` | Check if stack is empty | Return `true` |

The final output is `true`, indicating that the input string has valid parentheses.
## Code
```java
import java.util.Stack;

class Solution {
    public boolean isValid(String s) {
        Stack<Character> st = new Stack<>();

        for (char ch : s.toCharArray()) {
            if (ch == '(' || ch == '{' || ch == '[') {
                st.push(ch);
            } 
            else {
                if (st.isEmpty()) return false;

                char top = st.peek();

                if ((ch == ')' && top == '(') ||
                    (ch == '}' && top == '{') ||
                    (ch == ']' && top == '[')) {
                    st.pop();
                } else {
                    return false;
                }
            }
        }
        return st.empty();
    }
}

```