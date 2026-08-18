# 58. Length of Last Word

**LeetCode Problem:** [Length of Last Word](https://leetcode.com/problems/length-of-last-word/)

## Approach  
We scan the string from the end, first skipping any trailing spaces and then counting characters until we hit the next space (or the beginning of the string). The counted characters constitute the length of the last word.

### Step‑by‑step breakdown  

1. **Initialize** `length = 0` and set `i` to the index of the last character (`s.length() - 1`).  
2. **Skip trailing spaces** – while `i` is non‑negative and `s.charAt(i)` is a space, decrement `i`. This positions `i` on the last non‑space character (the end of the last word).  
3. **Count the last word** – while `i` is non‑negative and `s.charAt(i)` is **not** a space, increment `length` and decrement `i`. Each iteration processes one character of the last word.  
4. **Return** `length`, which now holds the number of characters in the last word (or `0` if the string contains no words).

- **Time Complexity**: **O(n)**, where *n* is the length of the string. Each character is examined at most once while moving the index `i` leftwards.  
- **Space Complexity**: **O(1)**, only a few integer variables are used regardless of the input size.

## Dry Run  

**Example input:** `"Hello World  "` (note the two trailing spaces)

| Step | `i` (index) | `length` | `s.charAt(i)` | Action taken | Result after action |
|------|------------|----------|---------------|--------------|---------------------|
| 0 (init) | 12 | 0 | – | Set `i = s.length() - 1` (points to last char) | `i = 12` (points to `' '` ) |
| 1 | 12 | 0 | `' '` | `while(i>=0 && s.charAt(i)==' ') i--` | `i = 11` |
| 2 | 11 | 0 | `' '` | Continue skipping spaces | `i = 10` |
| 3 | 10 | 0 | `'d'` | Exit first loop (found non‑space) | `i = 10` |
| 4 | 10 | 0 | `'d'` | `while(i>=0 && s.charAt(i)!=' ') { length++; i--; }` | `length = 1`, `i = 9` |
| 5 | 9 | 1 | `'l'` | Count character | `length = 2`, `i = 8` |
| 6 | 8 | 2 | `'r'` | Count character | `length = 3`, `i = 7` |
| 7 | 7 | 3 | `'o'` | Count character | `length = 4`, `i = 6` |
| 8 | 6 | 4 | `'W'` | Count character | `length = 5`, `i = 5` |
| 9 | 5 | 5 | `' '` | Exit second loop (hit a space) | `i = 5` |
| 10 | – | 5 | – | Return `length` | Output = **5** |

The algorithm correctly skips the trailing spaces, then counts the five letters of the last word `"World"` and returns `5`.
## Code
```java
class Solution {
    public int lengthOfLastWord(String s) {
        int length = 0;
        int i = s.length() - 1;
        
        while(i >= 0 && s.charAt(i) == ' '){
            i--;
        }
        while(i >= 0 && s.charAt(i) != ' '){
            length++;
            i--;
        }
        return length;
    }
}
```