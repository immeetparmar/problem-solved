# 151. Reverse Words in a String

**LeetCode Problem:** [Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/)

## Approach  
Trim the input string to remove leading/trailing spaces, split it into words using a regular expression that treats any amount of whitespace as a delimiter, then concatenate the words in reverse order with a single space between them.

### Step‑by‑step breakdown
1. **Trim the string** – `s.trim()` removes all leading and trailing whitespace characters.  
2. **Split into words** – `split("\\s+")` creates an array `words` where each element is a contiguous sequence of non‑whitespace characters.  
3. **Initialize a StringBuilder** – `ans` will hold the final reversed sentence.  
4. **Iterate backwards** – Loop from the last index of `words` down to `0`.  
5. **Append the current word** – Add `words[i]` to `ans`.  
6. **Add a separating space** – If the current word is not the first one (i ≠ 0), append a single space after it.  
7. **Return the result** – Convert `ans` to a `String` and return it.

- **Time Complexity**: **O(n)**, where *n* is the length of the input string. Trimming, splitting, and the single reverse traversal each scan the string once.  
- **Space Complexity**: **O(n)**, needed for the array of words and the `StringBuilder` that stores the output.

---

## Dry Run  

**Example input:** `"  the   sky   is   blue  "`  

| Step | Variables (`s`, `words`, `i`, `ans`) | Action taken | Result / Output |
|------|--------------------------------------|--------------|-----------------|
| 1 | `s = "  the   sky   is   blue  "` | `trim()` → removes leading/trailing spaces | `s = "the   sky   is   blue"` |
| 2 | `split("\\s+")` on trimmed `s` | creates array | `words = ["the","sky","is","blue"]` |
| 3 | `ans = ""` (empty `StringBuilder`) | initialization | – |
| 4 | `i = 3` (last index) | start backward loop | – |
| 5 | `ans.append(words[3])` → `"blue"` | append word | `ans = "blue"` |
| 6 | `i != 0` → true → `ans.append(" ")` | add space | `ans = "blue "` |
| 7 | `i = 2` | next iteration | – |
| 8 | `ans.append(words[2])` → `"is"` | append word | `ans = "blue is"` |
| 9 | `i != 0` → true → `ans.append(" ")` | add space | `ans = "blue is "` |
|10 | `i = 1` | next iteration | – |
|11 | `ans.append(words[1])` → `"sky"` | append word | `ans = "blue is sky"` |
|12 | `i != 0` → true → `ans.append(" ")` | add space | `ans = "blue is sky "` |
|13 | `i = 0` | next iteration | – |
|14 | `ans.append(words[0])` → `"the"` | append word | `ans = "blue is sky the"` |
|15 | `i == 0` → false → **no** space added | – |
|16 | Loop ends | – | – |
|17 | `return ans.toString()` | convert builder to string | **Output:** `"blue is sky the"` |

The algorithm correctly reverses the order of words while collapsing multiple spaces into a single separator.
## Code
```java

class Solution {
    public String reverseWords(String s) {
        String[] words = s.trim().split("\\s+");

        StringBuilder ans = new StringBuilder();

        for (int i = words.length - 1; i >= 0; i--) {
            ans.append(words[i]);

            if (i != 0) {
                ans.append(" ");
            }
        }

        return ans.toString();
    }
}
```