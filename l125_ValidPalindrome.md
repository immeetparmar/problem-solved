# 125. Valid Palindrome

**LeetCode Problem:** [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)

## Approach
The approach to solving the "Valid Palindrome" problem involves using a two-pointer technique, where two pointers, one starting from the beginning and one from the end of the string, move towards each other. This approach allows for efficient comparison of characters while ignoring non-alphanumeric characters and considering case insensitivity.
The algorithm iterates through the string, skipping non-alphanumeric characters and comparing characters at the current positions of the two pointers.

1. **Step 1**: Initialize two pointers, `l` and `r`, to the start and end of the string, respectively.
2. **Step 2**: Move the `l` pointer forward and the `r` pointer backward while skipping non-alphanumeric characters at both positions.
3. **Step 3**: Compare the characters at the current positions of `l` and `r` (case-insensitive).
4. **Step 4**: If the characters match, move both pointers towards the center of the string; otherwise, return false.
5. **Step 5**: Repeat steps 2-4 until the pointers meet or cross each other.

- **Time Complexity**: The time complexity is O(n), where n is the length of the input string, as each character is visited at most twice.
- **Space Complexity**: The space complexity is O(1), as only a constant amount of space is used to store the pointers and other variables.

## Dry Run
Let's consider the input string "A man, a plan, a canal: Panama" to demonstrate the algorithm.

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | l = 0, r = 30 | Initialize pointers | - |
| 2 | l = 0, r = 30 | Skip non-alphanumeric at l (0) | l = 0 (no change) |
| 3 | l = 0, r = 30 | Skip non-alphanumeric at r (30) | r = 29 |
| 4 | l = 0, r = 29 | Compare 'A' and 'a' (case-insensitive) | Match, l = 1, r = 28 |
| 5 | l = 1, r = 28 | Skip non-alphanumeric at l (1) | l = 2 |
| 6 | l = 2, r = 28 | Skip non-alphanumeric at r (28) | r = 27 |
| 7 | l = 2, r = 27 | Compare 'm' and 'm' (case-insensitive) | Match, l = 3, r = 26 |
| ... | ... | ... | ... |
| 15 | l = 15, r = 15 | Pointers cross, exit loop | Return true |

The algorithm returns true, indicating that the input string is a valid palindrome.
## Code
```java
class Solution {
    public boolean isPalindrome(String s) {
        int l = 0;
        int r = s.length() - 1;

        while (l < r) {
            
            while (l < r && !Character.isLetterOrDigit(s.charAt(l))) {
                l++;
            }

            while (l < r && !Character.isLetterOrDigit(s.charAt(r))) {
                r--;
            }

            if (Character.toLowerCase(s.charAt(l)) != Character.toLowerCase(s.charAt(r))) {
                return false;
            }

            l++;
            r--;
        }
        return true;
    }
}
```