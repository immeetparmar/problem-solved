# 1678. Goal Parser Interpretation

**LeetCode Problem:** [Goal Parser Interpretation](https://leetcode.com/problems/goal-parser-interpretation/)

## Approach  

Traverse the command string once, interpreting each symbol according to the rules:  
- **`G`** → `G`  
- **`()`** → `o`  
- **`(al)`** → `al`  

A `StringBuilder` collects the resulting characters while the index is advanced appropriately for the multi‑character patterns.

---

## Step‑by‑step breakdown  

1. **Initialize** a `StringBuilder` `sb` and set the loop index `i = 0`.  
2. **Read the current character** `c = command.charAt(i)`.  
3. **If `c` is `G`** – append `'G'` to `sb`.  
4. **If `c` is `'('` and the next character is `')'`** – it represents `()`.  
   * Append `'o'` to `sb`.  
   * Increment `i` by **1** extra (`i++`) to skip the closing parenthesis.  
5. **If `c` is `'('` and the next character is `'a'`** – it starts the pattern `(al)`.  
   * Append the string `"al"` to `sb`.  
   * Increment `i` by **3** extra (`i += 3`) to move past the characters `a`, `l`, and `)`.  
6. **Loop continues** until `i` reaches `command.length()`.  
7. **Return** `sb.toString()` as the interpreted result.

---

### Complexity  

- **Time Complexity:** **O(n)** – each character of the input string is examined at most once.  
- **Space Complexity:** **O(m)** – `sb` stores the output, whose length `m` is at most the length of the input (`m ≤ n`).  

---

## Dry Run  

**Example input:** `"(G)()((al)G)"` (interpreted as `G` `o` `al` `G` → `"GoalG"`)

| Step | `i` (index) | `c` (current char) | Action taken                                 | `sb` (output so far) |
|------|-------------|--------------------|----------------------------------------------|----------------------|
| 1    | 0           | `(`                | next char is `G` → not a pattern, fall‑through (no append) | `""` |
| 2    | 1           | `G`                | append `'G'`                                 | `"G"` |
| 3    | 2           | `)`                | none (already processed as part of previous step) | `"G"` |
| 4    | 3           | `(`                | next char is `)` → pattern `()` → append `'o'`, `i++` | `"Go"` |
| 5    | 5           | `(`                | next char is `(` → not a recognized pattern, skip | `"Go"` |
| 6    | 6           | `(`                | next char is `a` → pattern `(al)` → append `"al"`, `i+=3` | `"Goal"` |
| 7    | 10          | `G`                | append `'G'`                                 | `"GoalG"` |
| 8    | 11          | `)`                | none (closing parenthesis already consumed) | `"GoalG"` |
| 9    | 12 (= length) | –                | loop ends                                    | `"GoalG"` |

**Result:** `"GoalG"`  

The table shows how the index moves, which characters trigger which actions, and how the output is built step by step.
## Code
```java
class Solution {
    public String interpret(String command) {
        StringBuilder sb = new StringBuilder();

        for (int i = 0; i < command.length(); i++) {
            char c = command.charAt(i);

            if (c == 'G') {
                sb.append('G');
            } else if (c == '(' && command.charAt(i + 1) == ')') {
                sb.append('o');
                i++;
            } else if (c == '(' && command.charAt(i + 1) == 'a') {
                sb.append("al");
                i += 3;
            }
        }
        return sb.toString();   
    }
}
```