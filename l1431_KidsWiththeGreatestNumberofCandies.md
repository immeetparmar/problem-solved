# 1431. Kids With the Greatest Number of Candies

**LeetCode Problem:** [Kids With the Greatest Number of Candies](https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/)

## Approach

The approach involves finding the maximum number of candies any kid has and then checking for each kid if adding the extra candies would make their total greater than or equal to the maximum. This is done in two passes: one to find the maximum and another to compare each kid's candies plus the extra candies to the maximum.

Here is a step-by-step breakdown of the logic:
1. **Step 1**: Initialize a variable `max` to keep track of the maximum number of candies any kid has, starting with a value of 0.
2. **Step 2**: Iterate through the `candies` array to find the maximum number of candies. For each kid, if their candies are more than the current `max`, update `max` with that kid's candies.
3. **Step 3**: Create a new list `result` to store boolean values indicating whether each kid can have the greatest number of candies after receiving the extra candies.
4. **Step 4**: Iterate through the `candies` array again. For each kid, check if adding the `extraCandies` to their current candies would be greater than or equal to the `max` found earlier. Add the result of this comparison to the `result` list.

- **Time Complexity**: The time complexity is O(n), where n is the number of kids, because we make two passes through the `candies` array.
- **Space Complexity**: The space complexity is also O(n), where n is the number of kids, because we create a new list `result` that is as long as the `candies` array.

## Dry Run

Let's use the example input `candies = [2,3,5,1,3]` and `extraCandies = 3`.

| Step Number | Current State of Variables | Action Taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `max = 0`, `candies = [2,3,5,1,3]`, `extraCandies = 3` | Initialize `max` to 0 | `max = 0` |
| 2 | `max = 0`, `candies = [2,3,5,1,3]` | Find `max` in `candies`: `max = 5` | `max = 5` |
| 3 | `max = 5`, `candies = [2,3,5,1,3]`, `extraCandies = 3` | Create empty `result` list | `result = []` |
| 4 | `max = 5`, `candies = [2,3,5,1,3]`, `extraCandies = 3`, `result = []` | Check each kid: `2+3 >= 5` (False), `3+3 >= 5` (True), `5+3 >= 5` (True), `1+3 >= 5` (False), `3+3 >= 5` (True) | `result = [False, True, True, False, True]` |

The final output is `[False, True, True, False, True]`, indicating which kids can have the greatest number of candies after receiving the extra candies.
## Code
```java
class Solution {
    public List<Boolean> kidsWithCandies(int[] candies, int extraCandies) {
        int max = 0;

        for(int candy : candies){
            if(candy>max){
                max = candy;
            }
        }
            List<Boolean>result = new ArrayList<>();
            for(int candy : candies){
                result.add(candy + extraCandies >= max);
            }
        return result;
    }
}
```