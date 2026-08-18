# 1108. Defanging an IP Address

**LeetCode Problem:** [Defanging an IP Address](https://leetcode.com/problems/defanging-an-ip-address/)

## Approach  
Iterate through the characters of the input IP address, appending each character to a `StringBuilder`. Whenever a dot `'.'` is encountered, append the string `"[.]"` instead of the dot itself. Finally, convert the `StringBuilder` to a regular `String`.

### Step‑by‑step breakdown  

| # | Action |
|---|--------|
| **1** | Create an empty `StringBuilder` named `result`. |
| **2** | Convert the input string `address` to a character array and start a **for‑each** loop over the characters. |
| **3** | Inside the loop, check if the current character `c` is a dot `'.'`. |
| **4** | **If** `c` is a dot → append the literal string `"[.]"` to `result`. |
| **5** | **Else** (the character is a digit) → append the character `c` itself to `result`. |
| **6** | After the loop finishes, convert `result` to a regular `String` with `toString()` and return it. |

#### Complexity  

- **Time Complexity:** `O(n)` – each of the `n` characters in the input string is examined exactly once.  
- **Space Complexity:** `O(n)` – a new string of length up to `3·d + 2·(d‑1)` (where `d` is the number of digits) is built; in the worst case it is proportional to the input size.

---

## Dry Run  

**Example input:** `"192.168.0.1"`

| Step | `c` (current char) | `result` (content of StringBuilder) | Action |
|------|--------------------|--------------------------------------|--------|
| 0 (init) | – | `""` (empty) | `StringBuilder` created |
| 1 | `'1'` | `"1"` | Not a dot → append `'1'` |
| 2 | `'9'` | `"19"` | Not a dot → append `'9'` |
| 3 | `'2'` | `"192"` | Not a dot → append `'2'` |
| 4 | `'.'` | `"192[.]"` | Dot → append `"[.]"` |
| 5 | `'1'` | `"192[.]1"` | Not a dot → append `'1'` |
| 6 | `'6'` | `"192[.]16"` | Not a dot → append `'6'` |
| 7 | `'8'` | `"192[.]168"` | Not a dot → append `'8'` |
| 8 | `'.'` | `"192[.]168[.]"` | Dot → append `"[.]"` |
| 9 | `'0'` | `"192[.]168[.]0"` | Not a dot → append `'0'` |
|10 | `'.'` | `"192[.]168[.]0[.]"` | Dot → append `"[.]"` |
|11 | `'1'` | `"192[.]168[.]0[.]1"` | Not a dot → append `'1'` |

After processing all characters, `result.toString()` yields **`"192[.]168[.]0[.]1"`**, which is the correctly defanged IP address.
## Code
```java
class Solution {
    public String defangIPaddr(String address) { 
    StringBuilder result = new StringBuilder();

      for(char c :address.toCharArray()){
        if(c == '.'){
          result.append("[.]");
        } else{
          result.append(c);
        }
      }
      return result.toString();
    }
}
```