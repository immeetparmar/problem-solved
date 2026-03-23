# 189. Rotate Array

**LeetCode Problem:** [Rotate Array](https://leetcode.com/problems/rotate-array/)

## Approach
The approach to solving the "Rotate Array" problem involves using a series of swap operations to rotate the array in-place. This is achieved by first handling the case where the rotation count is greater than the array length, then swapping elements to achieve the rotation.

Here's a step-by-step breakdown:
1. **Step 1**: Calculate the effective rotation count by taking the modulus of the rotation count with the array length, ensuring the rotation count is within the bounds of the array length.
2. **Step 2**: Handle the edge case where the array has only one element, in which case no rotation is needed.
3. **Step 3**: Perform a swap operation on the entire array to reverse its order.
4. **Step 4**: Perform a swap operation on the first 'k' elements of the reversed array to reverse their order.
5. **Step 5**: Perform a swap operation on the remaining elements of the reversed array to reverse their order, resulting in the rotated array.

- **Time Complexity**: The time complexity of this solution is O(n), where n is the number of elements in the array, since we are potentially swapping every element in the array.
- **Space Complexity**: The space complexity of this solution is O(1), since we are only using a constant amount of space to store the indices and temporary swap variable.

## Dry Run

Let's take the example input `nums = [1, 2, 3, 4, 5, 6, 7]` and `k = 3`. Here's the step-by-step execution:

| Step Number | Current State of Variables | Action Taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `nums = [1, 2, 3, 4, 5, 6, 7]`, `k = 3` | Calculate effective rotation count: `k %= nums.length` | `k = 3` |
| 2 | `nums = [1, 2, 3, 4, 5, 6, 7]`, `k = 3` | Check for edge case: `if (n == 1) return` | No action taken |
| 3 | `nums = [1, 2, 3, 4, 5, 6, 7]`, `k = 3` | Swap entire array: `swap(nums, 0, n-1)` | `nums = [7, 6, 5, 4, 3, 2, 1]` |
| 4 | `nums = [7, 6, 5, 4, 3, 2, 1]`, `k = 3` | Swap first 'k' elements: `swap(nums, 0, k-1)` | `nums = [5, 6, 7, 4, 3, 2, 1]` |
| 5 | `nums = [5, 6, 7, 4, 3, 2, 1]`, `k = 3` | Swap remaining elements: `swap(nums, k, n-1)` | `nums = [5, 6, 7, 1, 2, 3, 4]` |

The final rotated array is `[5, 6, 7, 1, 2, 3, 4]`.
## Code
```java
class Solution {
    public static void rotate(int[] nums, int k) {
        int n = nums.length;
       // int abs = k % n;
        k%=nums.length;
        if(n==1) return;

        swap(nums, 0, n-1);
        swap(nums, 0, k-1);
        swap(nums, k, n-1);
       
        
    }

    public static void swap(int nums[], int left, int right){
        while(left<right){
            int temp = nums[left];
            nums[left] = nums[right];
            nums[right] = temp;
            left++;
            right--;
        }
    }
}
```