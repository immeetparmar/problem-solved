# 2864. Maximum Odd Binary Number

**LeetCode Problem:** [Maximum Odd Binary Number](https://leetcode.com/problems/maximum-odd-binary-number/)

## Approach  
The algorithm counts how many `'1'` characters are present, then builds the largest possible odd binary number by placing all but one of those `'1'`s at the most‑significant positions, filling the middle with `'0'`s, and finally appending a single `'1'` as the least‑significant bit (so the number is odd).

### Step‑by‑step breakdown  

1. **Count the ones** – Scan the input string `s` once and store the number of `'1'` characters in `count`.  
2. **Append leading ones** – Append `count‑1` `'1'` characters to a `StringBuilder`. These become the most significant bits.  
3. **Append zeros** – Append `(s.length() - count)` `'0'` characters. They occupy the middle positions.  
4. **Append the trailing one** – Append a single `'1'` to guarantee the binary number is odd.  
5. **Return the result** – Convert the `StringBuilder` to a `String` and return it.

---

- **Time Complexity**: `O(n)` – the string is traversed twice (once for counting, once for building), where `n = s.length()`.  
- **Space Complexity**: `O(n)` – a new string of length `n` is created to hold the result (the `StringBuilder`).

## Dry Run  

**Example input:** `s = "11010"`  

| Step | Variables (`count`, `result`) | Action taken | Result / Output |
|------|------------------------------|--------------|-----------------|
| 0 (initial) | `count = 0`, `result = ""` | – | – |
| 1 | Scan characters:<br>`'1'` → `count=1`<br>`'1'` → `count=2`<br>`'0'` → `count=2`<br>`'1'` → `count=3`<br>`'0'` → `count=3` | Count all `'1'`s | `count = 3` |
| 2 | `result = ""` | Append `count‑1 = 2` `'1'`s | `result = "11"` |
| 3 | `result = "11"` | Append `s.length() - count = 5 - 3 = 2` `'0'`s | `result = "1100"` |
| 4 | `result = "1100"` | Append trailing `'1'` | `result = "11001"` |
| 5 | `result = "11001"` | Return the built string | Output = **"11001"** |

The produced binary string `"11001"` is the maximum odd binary number that can be formed using the same multiset of bits as the original string.
## Code
```java
class Solution {
    public String maximumOddBinaryNumber(String s) {
        int count = 0;

        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == '1') {
                count++;
            }
        }
        StringBuilder result = new StringBuilder();

        for (int i = 0; i < count - 1; i++) {
            result.append('1');
        }
        for (int i = 0; i < s.length() - count; i++) {
            result.append('0');
        }
        result.append('1');

        return result.toString();
    }
}
```