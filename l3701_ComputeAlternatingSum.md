# 3701. Compute Alternating Sum

**LeetCode Problem:** [Compute Alternating Sum](https://leetcode.com/problems/compute-alternating-sum/)

## Approach

The approach to solving the "Compute Alternating Sum" problem involves iterating through the input array and alternately adding and subtracting elements from the sum. This is achieved by checking the index of each element and applying the corresponding operation.

Here's a step-by-step breakdown:
1. **Step 1**: Initialize a variable `sum` to 0, which will store the final alternating sum.
2. **Step 2**: Iterate through the input array `nums` using a for loop, keeping track of the current index `i`.
3. **Step 3**: For each element, check if the index `i` is even (i.e., `i % 2 == 0`). If it is, add the current element to the `sum`.
4. **Step 4**: If the index `i` is odd (i.e., `i % 2 != 0`), subtract the current element from the `sum`.
5. **Step 5**: After iterating through all elements, return the final `sum` as the result.

- **Time Complexity**: The time complexity of this solution is O(n), where n is the length of the input array, because we are iterating through the array once.
- **Space Complexity**: The space complexity is O(1), as we are only using a constant amount of space to store the `sum` variable.

## Dry Run

Let's consider an example input `nums = [1, 2, 3, 4, 5]`. Here's the step-by-step execution:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `sum = 0`, `i = 0`, `nums[0] = 1` | Add `nums[0]` to `sum` | `sum = 1` |
| 2 | `sum = 1`, `i = 1`, `nums[1] = 2` | Subtract `nums[1]` from `sum` | `sum = -1` |
| 3 | `sum = -1`, `i = 2`, `nums[2] = 3` | Add `nums[2]` to `sum` | `sum = 2` |
| 4 | `sum = 2`, `i = 3`, `nums[3] = 4` | Subtract `nums[3]` from `sum` | `sum = -2` |
| 5 | `sum = -2`, `i = 4`, `nums[4] = 5` | Add `nums[4]` to `sum` | `sum = 3` |

The final output is `3`, which is the alternating sum of the input array.
## Code
```java
class Solution {
    public int alternatingSum(int[] nums) {
        int sum = 0;

        for (int i = 0; i < nums.length; i++) {
            if (i % 2 == 0) {
                sum = sum + nums[i];
            } else {
                sum = sum - nums[i];
            }
        }
        return sum;
    }
}
```