# 1750. Minimum Length of String After Deleting Similar Ends

**LeetCode Problem:** [Minimum Length of String After Deleting Similar Ends](https://leetcode.com/problems/minimum-length-of-string-after-deleting-similar-ends/)

## Approach  

We use two‑pointer scanning from both ends of the string. While the characters at the left and right pointers are equal, we delete **all** consecutive occurrences of that character from both sides, then continue the comparison on the new ends. When the characters differ (or the pointers cross) the remaining substring cannot be reduced any further, and its length is the answer.

### Step‑by‑step breakdown  

| # | Description |
|---|-------------|
| 1 | Initialise `l = 0` (left pointer) and `r = s.length‑1` (right pointer). |
| 2 | If the string is `null` or empty, return `0`. |
| 3 | Enter the outer `while` loop: continue while `l < r` **and** `s.charAt(l) == s.charAt(r)`. This means the current ends are the same character and can potentially be removed. |
| 4 | Store the common character in `ch = s.charAt(l)`. |
| 5 | **Delete from the left** – move `l` rightwards while `l ≤ r` and `s.charAt(l) == ch`. Each increment skips one occurrence of `ch`. |
| 6 | **Delete from the right** – move `r` leftwards while `l ≤ r` and `s.charAt(r) == ch`. Each decrement skips one occurrence of `ch`. |
| 7 | After both inner loops finish, go back to step 3 to check the new ends. |
| 8 | When the outer loop stops, the characters at `l` and `r` are different (or the pointers have crossed). The smallest possible remaining string is the substring `s[l…r]`. Its length is `r - l + 1`. Return this value. |

---

### Complexity  

- **Time Complexity:** `O(n)` – each character is examined at most once by the left or right pointer, so the total work is linear in the length of the string `n`.  
- **Space Complexity:** `O(1)` – only a few integer variables are used, independent of input size.

---

## Dry Run  

**Example input:** `s = "aabccbaa"`  

| Step | `l` | `r` | `s.charAt(l)` | `s.charAt(r)` | Action | New `l` | New `r` |
|------|-----|-----|---------------|---------------|--------|---------|---------|
| 0 (init) | 0 | 7 | `a` | `a` | – | 0 | 7 |
| 1 | 0 | 7 | `a` | `a` | outer condition true (`a` == `a`) → `ch = 'a'` | – | – |
| 2 | 0→1→2 | 7 | `a` → `b` (stop) | `a` | delete left `a`s while `s[l]==ch` | `l = 2` | 7 |
| 3 | 2 | 7→6→5→4 | `b` | `a` → `b` (stop) | delete right `a`s while `s[r]==ch` | 2 | `r = 4` |
| 4 | 2 | 4 | `b` | `b` | outer condition true (`b` == `b`) → `ch = 'b'` | – | – |
| 5 | 2→3 | 4 | `c` (stop) | `b` → `c` (stop) | delete left `b`s | `l = 3` | 4 |
| 6 | 3 | 4→3 | `c` | `c` (stop) | delete right `b`s (none) – `r` moves while `s[r]==ch` (`b` not equal) → no change | 3 | 4 |
| 7 | 3 | 4 | `c` | `c` | outer condition true (`c` == `c`) → `ch = 'c'` | – | – |
| 8 | 3→4→5 | 4→3 | (pointers cross) | – | delete left `c`s, then delete right `c`s | `l = 5` | `r = 3` |
| 9 | 5 | 3 | – | – | outer loop ends (`l ≥ r`) | – | – |
| 10 | – | – | – | – | Result length = `r - l + 1 = 3 - 5 + 1 = 0` | – | – |

**Result:** The minimum possible length is `0`, which matches the expected answer for `"aabccbaa"` (the whole string can be removed).
## Code
```java
class Solution {
    public int minimumLength(String s) {
         int l = 0;
        int r = s.length() - 1;

        if (s == null || s.isEmpty()) {
            return 0;
        }

        while (l < r && s.charAt(l) == s.charAt(r)) {
            char ch = s.charAt(l);

            while (l <= r && s.charAt(l) == ch) {
                l++;
            }
            while (l <= r && s.charAt(r) == ch) {
                r--;
            }
        }
        return r - l + 1;
    }
}
```