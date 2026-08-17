# 1662. Check If Two String Arrays are Equivalent

**LeetCode Problem:** [Check If Two String Arrays are Equivalent](https://leetcode.com/problems/check-if-two-string-arrays-are-equivalent/)

## Approach

This solution solves the "Check If Two String Arrays are Equivalent" problem.

**Time Complexity:** To be analyzed  
**Space Complexity:** To be analyzed

---

> [!NOTE]
> **AI explanation generation failed**  
> Reason: 404 This model models/gemini-2.5-flash is no longer available to new users. Please update your code 
> 
> Please add a detailed explanation manually, or wait for API quota to reset and re-run the sync.

## Code
```java
class Solution {
    public boolean arrayStringsAreEqual(String[] word1, String[] word2) {

        StringBuilder s1 = new StringBuilder();
        StringBuilder s2 = new StringBuilder();

        for (String s : word1) {
            s1.append(s);
        }

        for (String s : word2) {
            s2.append(s);
        }

        return s1.toString().equals(s2.toString());
    }
}
```