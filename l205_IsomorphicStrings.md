# 205. Isomorphic Strings

**LeetCode Problem:** [Isomorphic Strings](https://leetcode.com/problems/isomorphic-strings/)

## Approach  

Use two fixed‑size integer arrays to record the *last position* (plus one) where each character was seen in the two strings.  
If at any index the recorded positions differ, the mapping between characters is inconsistent, so the strings are not isomorphic.

### Step‑by‑step breakdown  

1. **Initialize mapping arrays** – Create two integer arrays `m1` and `m2` of length 256 (enough for all ASCII characters). All entries start at 0, meaning “character not seen yet”.  
2. **Iterate over the strings** – For each index `i` from `0` to `s.length‑1` (the strings have equal length by problem statement):  
   a. Retrieve the current characters `c1 = s.charAt(i)` and `c2 = t.charAt(i)`.  
   b. **Check consistency** – Compare `m1[c1]` with `m2[c2]`.  
      - If they differ, the previous occurrence positions of `c1` and `c2` do not match, so the mapping is broken → return `false`.  
   c. **Record the current position** – Store `i+1` (using `+1` to distinguish from the initial 0) in both arrays: `m1[c1] = i+1` and `m2[c2] = i+1`.  
3. **Finish loop** – If the loop completes without a mismatch, every character pair respects a one‑to‑one mapping. Return `true`.

### Complexity  

- **Time Complexity**: `O(n)` where `n = s.length()`. Each character is processed once and all array accesses are `O(1)`.  
- **Space Complexity**: `O(1)` because the two mapping arrays have a constant size of 256 regardless of input length.

---

## Dry Run  

**Example**: `s = "paper"`, `t = "title"`  

| Step | `i` | `c1` (`s.charAt(i)`) | `c2` (`t.charAt(i)`) | `m1[c1]` before | `m2[c2]` before | Comparison `m1[c1] != m2[c2]` | Action | `m1[c1]` after | `m2[c2]` after |
|------|-----|----------------------|----------------------|-----------------|-----------------|-------------------------------|--------|----------------|----------------|
| 1    | 0   | p                    | t                    | 0               | 0               | false                         | record | 1              | 1              |
| 2    | 1   | a                    | i                    | 0               | 0               | false                         | record | 2              | 2              |
| 3    | 2   | p                    | t                    | 1               | 1               | false                         | record | 3              | 3              |
| 4    | 3   | e                    | l                    | 0               | 0               | false                         | record | 4              | 4              |
| 5    | 4   | r                    | e                    | 0               | 0               | false                         | record | 5              | 5              |

No step triggered a `false` return, so after the loop the algorithm returns **`true`**, correctly indicating that `"paper"` and `"title"` are isomorphic.
## Code
```java
class Solution {
    public boolean isIsomorphic(String s, String t) {
        int[] m1 = new int[256];
        int[] m2 = new int[256];

        for (int i = 0; i < s.length(); i++) {
            char s1 = s.charAt(i);
            char s2 = t.charAt(i);

            if (m1[s1] != m2[s2]) {
                return false;
            }
            m1[s1] = i + 1;
            m2[s2] = i + 1;
        }
        return true;
    }
}
```