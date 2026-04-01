# 27. Remove Element

**LeetCode Problem:** [Remove Element](https://leetcode.com/problems/remove-element/)

## Approach
The approach used to solve the "Remove Element" problem is a two-pointer technique, where one pointer iterates through the array and the other pointer keeps track of the position where the next element that is not equal to the target value should be placed. This approach allows for an efficient removal of elements from the array in a single pass.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Initialize two pointers, `i` and `j`, to the beginning of the array, where `i` will keep track of the position of the next element that is not equal to the target value, and `j` will iterate through the array.
2. **Step 2**: Iterate through the array using the `j` pointer, and for each element, check if it is not equal to the target value.
3. **Step 3**: If the current element is not equal to the target value, place it at the position pointed to by `i` and increment `i` to point to the next position.
4. **Step 4**: Continue iterating through the array until all elements have been processed.
5. **Step 5**: The final value of `i` will be the new length of the array, which represents the number of elements that are not equal to the target value.

- **Time Complexity**: The time complexity of this approach is O(n), where n is the length of the input array, because we are iterating through the array only once.
- **Space Complexity**: The space complexity of this approach is O(1), because we are not using any additional space that scales with the input size, only a constant amount of space to store the pointers and the target value.

## Dry Run
Let's consider an example input `nums = [3, 2, 2, 3]` and `val = 3`. Here's a step-by-step execution of the algorithm:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `i = 0`, `j = 0`, `nums = [3, 2, 2, 3]` | Check if `nums[j] != val` | `nums[j] == val`, do nothing |
| 2 | `i = 0`, `j = 1`, `nums = [3, 2, 2, 3]` | Check if `nums[j] != val` | `nums[j] != val`, `nums[i] = nums[j]`, `i++` | `i = 1`, `nums = [2, 2, 2, 3]` |
| 3 | `i = 1`, `j = 2`, `nums = [2, 2, 2, 3]` | Check if `nums[j] != val` | `nums[j] != val`, `nums[i] = nums[j]`, `i++` | `i = 2`, `nums = [2, 2, 2, 3]` |
| 4 | `i = 2`, `j = 3`, `nums = [2, 2, 2, 3]` | Check if `nums[j] != val` | `nums[j] == val`, do nothing |
| 5 | `i = 2`, `j = 4`, `nums = [2, 2, 2, 3]` | End of iteration | Return `i` as the new length | `i = 2` |

After the execution, the modified array is `[2, 2, 2, 3]` and the new length is `2`, which represents the number of elements that are not equal to the target value `3`.
## Code
```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int i = 0;

        for(int j = 0; j < nums.length; j++){
            if(nums[j] != val){
                nums[i] = nums[j];
                i++;
            }
        }

        return i;
    }
}
```