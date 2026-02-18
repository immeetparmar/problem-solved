# 1688. Count of Matches in Tournament

**LeetCode Problem:** [Count of Matches in Tournament](https://leetcode.com/problems/count-of-matches-in-tournament/)

## Approach
The approach to solving the "Count of Matches in Tournament" problem involves recognizing that in a single-elimination tournament, the number of matches played is always one less than the number of teams participating. This is because each match eliminates one team, and the tournament continues until only one team remains.

Here is a step-by-step breakdown of the logic:
1. **Step 1**: Recognize that the problem is asking for the total number of matches in a tournament with n teams.
2. **Step 2**: Understand that in a single-elimination tournament, each match eliminates one team, and the tournament continues until only one team remains.
3. **Step 3**: Deduce that the total number of matches is equal to the number of teams minus one, because each match eliminates one team and the last team standing is the winner.

- **Time Complexity**: The time complexity of this solution is O(1), because it involves a constant-time operation regardless of the input size.
- **Space Complexity**: The space complexity of this solution is O(1), because it uses a constant amount of space to store the input and output.

## Dry Run
Let's consider an example with 5 teams. Here's how the algorithm would execute:

| Step Number | Current State of Variables | Action Taken | Result/Output |
|-------------|----------------------------|--------------|---------------|
| 1           | n = 5                      | Recognize the problem and the formula to solve it | -             |
| 2           | n = 5                      | Apply the formula: number of matches = n - 1 | number of matches = 4 |
| 3           | number of matches = 4       | Return the result | Output: 4      |

In this example, the algorithm correctly calculates that a tournament with 5 teams will have 4 matches.
## Code
```java
class Solution {
    public int numberOfMatches(int n) {
        return n-1;
    }
}
```