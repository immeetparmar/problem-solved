# 1089. Duplicate Zeros

**LeetCode Problem:** [Duplicate Zeros](https://leetcode.com/problems/duplicate-zeros/)

## Approach

The approach to solving this problem involves iterating over the input array and shifting elements to the right whenever a zero is encountered, effectively duplicating the zero. This is achieved through a nested loop structure that handles the shifting of elements.

Here is a step-by-step breakdown of the logic:
1. **Step 1**: Iterate over the input array from the first element to the second last element.
2. **Step 2**: Check if the current element is zero. If it's not, move on to the next element.
3. **Step 3**: If the current element is zero, shift all elements to its right one position to the right, starting from the last element.
4. **Step 4**: After shifting, place a zero in the position immediately after the original zero.
5. **Step 5**: Increment the loop counter to skip the newly inserted zero in the next iteration.

- **Time Complexity**: The time complexity of this solution is O(n^2) because in the worst case, for each element in the array, we might have to shift all the remaining elements.
- **Space Complexity**: The space complexity is O(1) because we are modifying the input array in-place and not using any additional space that scales with the input size.

## Dry Run

Let's consider the input array `[1, 0, 2, 3, 0, 4, 5, 0]`. Here's how the algorithm would execute:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `i = 0`, `arr = [1, 0, 2, 3, 0, 4, 5, 0]` | Check if `arr[0]` is zero. It's not, move to the next element. | `i = 1`, `arr = [1, 0, 2, 3, 0, 4, 5, 0]` |
| 2 | `i = 1`, `arr = [1, 0, 2, 3, 0, 4, 5, 0]` | `arr[1]` is zero, shift elements to the right. | `i = 1`, `arr = [1, 0, 0, 3, 0, 4, 5, 0]` (after shifting) |
| 3 | `i = 2`, `arr = [1, 0, 0, 3, 0, 4, 5, 0]` | Check if `arr[2]` is zero. It's not, move to the next element. | `i = 3`, `arr = [1, 0, 0, 3, 0, 4, 5, 0]` |
| 4 | `i = 3`, `arr = [1, 0, 0, 3, 0, 4, 5, 0]` | Check if `arr[3]` is zero. It's not, move to the next element. | `i = 4`, `arr = [1, 0, 0, 3, 0, 4, 5, 0]` |
| 5 | `i = 4`, `arr = [1, 0, 0, 3, 0, 4, 5, 0]` | `arr[4]` is zero, shift elements to the right. | `i = 4`, `arr = [1, 0, 0, 3, 0, 0, 5, 0]` (after shifting) |
| 6 | `i = 5`, `arr = [1, 0, 0, 3, 0, 0, 5, 0]` | Check if `arr[5]` is zero. It's not, move to the next element. | `i = 6`, `arr = [1, 0, 0, 3, 0, 0, 5, 0]` |
| 7 | `i = 6`, `arr = [1, 0, 0, 3, 0, 0, 5, 0]` | Check if `arr[6]` is zero. It's not, move to the next element. | `i = 7`, `arr = [1, 0, 0, 3, 0, 0, 5, 0]` |
| 8 | `i = 7`, `arr = [1, 0, 0, 3, 0, 0, 5, 0]` | `arr[7]` is zero, but we are at the end of the array, so we stop. | Final `arr = [1, 0, 0, 3, 0, 0, 5, 0]` |

The final output of the algorithm for the input `[1, 0, 2, 3, 0, 4, 5, 0]` is `[1, 0, 0, 3, 0, 0, 5, 0]`.
## Code
```java
class Solution {
    public void duplicateZeros(int[] arr) {

        for (int i = 0; i < arr.length - 1; i++) {
            if (arr[i] == 0) {
                for (int j = arr.length - 1; j > i; j--) {
                    arr[j] = arr[j - 1];
                }
                arr[i + 1] = 0;
                i++;
            }
        }
    }
}
```