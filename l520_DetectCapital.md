# 520. Detect Capital

**LeetCode Problem:** [Detect Capital](https://leetcode.com/problems/detect-capital/)

## Approach  
Count how many capital letters appear in the word and then verify whether this count matches one of the three allowed capital‑usage patterns: all lower‑case, all upper‑case, or only the first character capitalised.

### Step‑by‑step breakdown
1. **Initialize counter** – Set `count = 0` to hold the number of uppercase characters.  
2. **Traverse the string** – Loop over each character of `word`.  
3. **Check case** – For each character, use `Character.isUpperCase`; if it is uppercase, increment `count`.  
4. **All lower‑case test** – After the loop, if `count == 0` the word contains no capitals → return `true`.  
5. **All upper‑case test** – If `count == word.length()` the whole word is capitalised → return `true`.  
6. **Single leading capital test** – If exactly one capital exists **and** it is at position 0 (`Character.isUpperCase(word.charAt(0))`) → return `true`.  
7. **Invalid pattern** – If none of the above conditions hold, the word violates the rule → return `false`.

- **Time Complexity**: `O(n)` where *n* is the length of the input word, because we scan the string once.  
- **Space Complexity**: `O(1)` – only a few primitive variables are used regardless of input size.

---

## Dry Run  

**Example input:** `"Google"`

| Step | Variables (`count`, `i`, `word.charAt(i)`) | Action | Result / Output |
|------|-------------------------------------------|--------|-----------------|
| 1    | `count = 0`                               | Initialise counter | — |
| 2    | `i = 0`, `word.charAt(0) = 'G'` (upper)   | `isUpperCase` true → `count++` | `count = 1` |
| 3    | `i = 1`, `word.charAt(1) = 'o'` (lower)   | `isUpperCase` false | `count = 1` |
| 4    | `i = 2`, `word.charAt(2) = 'o'` (lower)   | `isUpperCase` false | `count = 1` |
| 5    | `i = 3`, `word.charAt(3) = 'g'` (lower)   | `isUpperCase` false | `count = 1` |
| 6    | `i = 4`, `word.charAt(4) = 'l'` (lower)   | `isUpperCase` false | `count = 1` |
| 7    | `i = 5`, `word.charAt(5) = 'e'` (lower)   | `isUpperCase` false | `count = 1` |
| 8    | Loop ends (`i == word.length()`)          | Exit loop | `count = 1` |
| 9    | `count == 0`? → **false**                 | Check all‑lower case | — |
| 10   | `count == word.length()`? → **false**     | Check all‑upper case | — |
| 11   | `count == 1 && word.charAt(0) upper?` → **true** | Single leading capital condition satisfied | **return `true`** |
| 12   | Function ends                              | — | **Output:** `true` (capital usage is correct) |

The table shows how the algorithm counts one capital letter at the first position and then validates the “only first letter capitalised” rule, yielding the correct result.
## Code
```java
class Solution {
    public boolean detectCapitalUse(String word) {

        int count = 0;

        for (int i = 0; i < word.length(); i++) {

            if (Character.isUpperCase(word.charAt(i))) {
                count++;
            }
        }

        if (count == 0) {
            return true;
        }

        if (count == word.length()) {
            return true;
        }
        if (count == 1 && Character.isUpperCase(word.charAt(0))) {
            return true;
        }
        
        return false;
    }
}
```