# 268. Missing Number

**LeetCode Problem:** [Missing Number](https://leetcode.com/problems/missing-number/)

## Approach
The approach to solving the "Missing Number" problem involves calculating the sum of all numbers from 0 to n (where n is the length of the input array) and then subtracting the sum of the numbers in the input array. This is based on the formula for the sum of an arithmetic series, which is n * (n + 1) / 2.

Here is a step-by-step breakdown of the logic:
1. **Step 1**: Calculate the length of the input array and store it in the variable `n`.
2. **Step 2**: Calculate the sum of all numbers from 0 to `n` using the formula `n * (n + 1) / 2` and store it in the variable `sum`.
3. **Step 3**: Iterate over each number in the input array, subtracting it from the `sum` variable.
4. **Step 4**: After iterating over all numbers, the `sum` variable will hold the missing number, which is then returned as the result.

- **Time Complexity**: The time complexity of this solution is O(n), where n is the length of the input array, because we are iterating over the array once.
- **Space Complexity**: The space complexity of this solution is O(1), because we are using a constant amount of space to store the variables `n` and `sum`, regardless of the size of the input array.

## Dry Run
Let's take the example input `nums = [0, 1, 3]`. Here is the execution of the algorithm in a structured table format:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `n = 3`, `sum = ?` | Calculate `n` and initialize `sum` | `n = 3`, `sum = ?` |
| 2 | `n = 3`, `sum = ?` | Calculate `sum = n * (n + 1) / 2` | `n = 3`, `sum = 6` |
| 3 | `n = 3`, `sum = 6`, `num = 0` | Subtract `num` from `sum` | `n = 3`, `sum = 6`, `num = 0`, `sum = 6` |
| 3 | `n = 3`, `sum = 6`, `num = 1` | Subtract `num` from `sum` | `n = 3`, `sum = 5`, `num = 1` |
| 3 | `n = 3`, `sum = 5`, `num = 3` | Subtract `num` from `sum` | `n = 3`, `sum = 2`, `num = 3` |
| 4 | `n = 3`, `sum = 2` | Return `sum` as the missing number | `missing number = 2` |

The final result is `2`, which is the missing number in the input array.
## Code
```java
class Solution {
    public int missingNumber(int[] nums) {
        int n = nums.length;
        int sum = n * (n + 1) / 2;

        for(int num : nums){
            sum -= num;
        }

        return sum;
    }
}
```