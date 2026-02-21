# 485. Max Consecutive Ones

**LeetCode Problem:** [Max Consecutive Ones](https://leetcode.com/problems/max-consecutive-ones/)

## Approach

The approach to solving the "Max Consecutive Ones" problem involves iterating through the input array and keeping track of the maximum consecutive count of ones encountered so far. The algorithm uses two variables, `count` and `max`, to achieve this.

Here is a step-by-step breakdown of the logic:
1. **Step 1**: Initialize two variables, `count` and `max`, to keep track of the current consecutive count of ones and the maximum consecutive count encountered so far, respectively.
2. **Step 2**: Iterate through the input array, checking each element to see if it's equal to 1.
3. **Step 3**: If the current element is 1, increment the `count` variable and update `max` if `count` is greater than `max`.
4. **Step 4**: If the current element is not 1, reset the `count` variable to 0, effectively starting a new count for the next sequence of consecutive ones.

- **Time Complexity**: The time complexity of this algorithm is O(n), where n is the length of the input array, because it involves a single pass through the array.
- **Space Complexity**: The space complexity is O(1), as it uses a constant amount of space to store the `count` and `max` variables, regardless of the input size.

## Dry Run

Let's consider the input array `[1, 1, 0, 1, 1, 1]`. Here's how the algorithm would execute:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | count = 0, max = 0 | Initialize variables | count = 0, max = 0 |
| 2 | count = 0, max = 0 | Check nums[0] == 1, increment count | count = 1, max = 0 |
| 3 | count = 1, max = 0 | Check nums[1] == 1, increment count and update max | count = 2, max = 2 |
| 4 | count = 2, max = 2 | Check nums[2] == 0, reset count | count = 0, max = 2 |
| 5 | count = 0, max = 2 | Check nums[3] == 1, increment count | count = 1, max = 2 |
| 6 | count = 1, max = 2 | Check nums[4] == 1, increment count | count = 2, max = 2 |
| 7 | count = 2, max = 2 | Check nums[5] == 1, increment count and update max | count = 3, max = 3 |
| 8 | count = 3, max = 3 | End of array, return max | Output: 3 |
## Code
```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
      int count = 0 ;
       int max = 0 ;
        for(int i = 0; i<nums.length;i++){
            if (nums[i]== 1){
                count ++;

            if (count > max) {
                    max = count;
             } } 
                else{
                    count = 0;
                }
       }
       return max;
    }
}
```