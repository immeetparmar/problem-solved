# 2089. Find Target Indices After Sorting Array

**LeetCode Problem:** [Find Target Indices After Sorting Array](https://leetcode.com/problems/find-target-indices-after-sorting-array/)

## Approach
The approach to solving the "Find Target Indices After Sorting Array" problem involves sorting the input array and then iterating through it to find the indices of the target element. This is achieved by utilizing Java's built-in sorting functionality and a simple loop to identify the target indices.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Sort the input array in ascending order using the `Arrays.sort()` method.
2. **Step 2**: Initialize an empty list to store the indices of the target element.
3. **Step 3**: Iterate through the sorted array, comparing each element to the target element.
4. **Step 4**: If an element matches the target, add its index to the result list.
5. **Step 5**: After iterating through the entire array, return the list of indices.

- **Time Complexity**: The time complexity of this solution is O(n log n) due to the sorting operation, where n is the number of elements in the input array.
- **Space Complexity**: The space complexity is O(n) for storing the result list in the worst-case scenario, where all elements in the array are equal to the target.

## Dry Run
Let's consider an example input: `nums = [1, 2, 5, 2, 3]` and `target = 2`.

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `nums = [1, 2, 5, 2, 3]` | Sort the array using `Arrays.sort()` | `nums = [1, 2, 2, 3, 5]` |
| 2 | `nums = [1, 2, 2, 3, 5]`, `result = []` | Initialize an empty list to store indices | `result = []` |
| 3 | `nums = [1, 2, 2, 3, 5]`, `result = []` | Start iterating through the array | - |
| 4 | `nums = [1, 2, 2, 3, 5]`, `result = []`, `i = 0` | Compare `nums[0]` to the target | `nums[0]` is not equal to the target |
| 5 | `nums = [1, 2, 2, 3, 5]`, `result = []`, `i = 1` | Compare `nums[1]` to the target | `nums[1]` is equal to the target, add index 1 to the result list |
| 6 | `nums = [1, 2, 2, 3, 5]`, `result = [1]`, `i = 2` | Compare `nums[2]` to the target | `nums[2]` is equal to the target, add index 2 to the result list |
| 7 | `nums = [1, 2, 2, 3, 5]`, `result = [1, 2]`, `i = 3` | Compare `nums[3]` to the target | `nums[3]` is not equal to the target |
| 8 | `nums = [1, 2, 2, 3, 5]`, `result = [1, 2]`, `i = 4` | Compare `nums[4]` to the target | `nums[4]` is not equal to the target |
| 9 | `nums = [1, 2, 2, 3, 5]`, `result = [1, 2]` | End of iteration, return the result list | `result = [1, 2]` |

The final output for the given example is `[1, 2]`, which represents the indices of the target element `2` in the sorted array.
## Code
```java
import java.util.*;

class Solution {
    public List<Integer> targetIndices(int[] nums, int target) {
        Arrays.sort(nums);

        List<Integer> result = new ArrayList<>();
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == target) {
                result.add(i);
            }
        }
        return result;
    }
}
```