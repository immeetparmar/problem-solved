# 283. Move Zeroes

**LeetCode Problem:** [Move Zeroes](https://leetcode.com/problems/move-zeroes/)

## Approach

The approach to solving the "Move Zeroes" problem involves iterating through the input array and swapping non-zero elements with the first zero encountered, effectively moving all zeroes to the end of the array. This is achieved by maintaining a pointer to the next non-zero position and swapping elements as needed.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Initialize a pointer `Zero` to 0, which keeps track of the next position where a non-zero element should be placed.
2. **Step 2**: Iterate through the input array `nums` using a for loop, checking each element to see if it's non-zero.
3. **Step 3**: If a non-zero element is found, swap it with the element at the current `Zero` index, then increment the `Zero` pointer to point to the next position.
4. **Step 4**: Continue iterating through the array until all elements have been checked.

- **Time Complexity**: The time complexity of this solution is O(n), where n is the length of the input array, as each element is visited once.
- **Space Complexity**: The space complexity is O(1), as only a constant amount of space is used to store the `Zero` pointer and temporary swap variable.

## Dry Run

Let's use the input array `[0, 1, 0, 3, 12]` as an example:

| Step Number | Current State of Variables | Action Taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `Zero = 0`, `i = 0`, `nums = [0, 1, 0, 3, 12]` | Check if `nums[0]` is non-zero | No swap, `i` increments |
| 2 | `Zero = 0`, `i = 1`, `nums = [0, 1, 0, 3, 12]` | Swap `nums[1]` with `nums[Zero]` | `nums = [1, 0, 0, 3, 12]`, `Zero` increments to 1 |
| 3 | `Zero = 1`, `i = 2`, `nums = [1, 0, 0, 3, 12]` | Check if `nums[2]` is non-zero | No swap, `i` increments |
| 4 | `Zero = 1`, `i = 3`, `nums = [1, 0, 0, 3, 12]` | Swap `nums[3]` with `nums[Zero]` | `nums = [1, 3, 0, 0, 12]`, `Zero` increments to 2 |
| 5 | `Zero = 2`, `i = 4`, `nums = [1, 3, 0, 0, 12]` | Swap `nums[4]` with `nums[Zero]` | `nums = [1, 3, 12, 0, 0]`, `Zero` increments to 3 |
| 6 | `Zero = 3`, `i = 5`, `nums = [1, 3, 12, 0, 0]` | End of iteration | Final result: `nums = [1, 3, 12, 0, 0]` |
## Code
```java
class Solution {
    public void moveZeroes(int[] nums) {
        int Zero = 0; 

        for(int i = 0; i < nums.length; i++){
            if(nums[i] != 0){
                int temp = nums[i];
                nums[i] = nums[Zero];
                nums[Zero] = temp;
                Zero++;
            }
        }
    }
}
```