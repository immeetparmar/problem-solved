# 217. Contains Duplicate

**LeetCode Problem:** [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)

## Approach
The approach to solving the "Contains Duplicate" problem involves utilizing a HashSet to keep track of the elements encountered in the array. This allows for efficient lookups and insertions, enabling the algorithm to determine if any duplicates exist in the array.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Initialize an empty HashSet to store unique elements from the input array.
2. **Step 2**: Iterate through each element in the input array, checking if the current element already exists in the HashSet.
3. **Step 3**: If the current element is found in the HashSet, immediately return true, indicating the presence of a duplicate.
4. **Step 4**: If the current element is not in the HashSet, add it to the set and continue with the next element in the array.
5. **Step 5**: If the iteration completes without finding any duplicates, return false, indicating that no duplicates exist in the array.

- **Time Complexity**: The time complexity of this algorithm is O(n), where n is the number of elements in the input array, because each element is processed once and HashSet operations (add and contains) take constant time on average.
- **Space Complexity**: The space complexity is O(n) as well, because in the worst-case scenario (all unique elements), the size of the HashSet will be equal to the number of elements in the input array.

## Dry Run
Let's consider the input array `[1, 2, 3, 1]`. Here's the step-by-step execution:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `set = {}`, `nums = [1, 2, 3, 1]` | Initialize HashSet | `set = {}` |
| 2 | `set = {}`, `num = 1` | Check if 1 is in set, add 1 to set | `set = {1}` |
| 3 | `set = {1}`, `num = 2` | Check if 2 is in set, add 2 to set | `set = {1, 2}` |
| 4 | `set = {1, 2}`, `num = 3` | Check if 3 is in set, add 3 to set | `set = {1, 2, 3}` |
| 5 | `set = {1, 2, 3}`, `num = 1` | Check if 1 is in set, return true | `true` |

The algorithm returns `true` after the fifth step, indicating that the input array contains a duplicate.
## Code
```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> set = new HashSet<>();

        for(int num : nums){
            if(set.contains(num)){
                return true;
            }
            set.add(num);
        }
        return false;
    }
}
```