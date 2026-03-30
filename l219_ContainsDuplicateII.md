# 219. Contains Duplicate II

**LeetCode Problem:** [Contains Duplicate II](https://leetcode.com/problems/contains-duplicate-ii/)

## Approach
The approach to solving the "Contains Duplicate II" problem involves using a sliding window technique with a HashSet to keep track of unique elements within a certain distance `k`. This allows for efficient checking of duplicates within the specified range.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Initialize an empty HashSet to store unique elements within the current window.
2. **Step 2**: Iterate through the input array, checking if the current element is already present in the HashSet. If it is, return `true` as a duplicate is found within the distance `k`.
3. **Step 3**: Add the current element to the HashSet.
4. **Step 4**: If the size of the HashSet exceeds `k`, remove the oldest element from the HashSet to maintain a window size of `k`.
5. **Step 5**: If the iteration completes without finding any duplicates within the distance `k`, return `false`.

- **Time Complexity**: The time complexity of this solution is O(n), where n is the number of elements in the input array, as each element is processed once.
- **Space Complexity**: The space complexity is O(k), as in the worst-case scenario, the HashSet will store up to `k` unique elements.

## Dry Run
Let's consider the example input `nums = [1, 2, 3, 1]` and `k = 3`. Here's the execution in a structured table format:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `set = []`, `i = 0`, `nums[i] = 1` | Add 1 to set | `set = [1]` |
| 2 | `set = [1]`, `i = 1`, `nums[i] = 2` | Add 2 to set | `set = [1, 2]` |
| 3 | `set = [1, 2]`, `i = 2`, `nums[i] = 3` | Add 3 to set | `set = [1, 2, 3]` |
| 4 | `set = [1, 2, 3]`, `i = 3`, `nums[i] = 1` | Check if 1 is in set | `1 is in set`, return `true` |

The algorithm returns `true` as a duplicate (1) is found within the distance `k = 3`.
## Code
```java
import java.util.HashSet;

class Solution {
    public boolean containsNearbyDuplicate(int[] nums, int k) {
        HashSet<Integer> set = new HashSet<>();

    for (int i = 0; i < nums.length; i++) {
            if (set.contains(nums[i])) {
                return true;
            }
            set.add(nums[i]);
            if (set.size() > k) {
                set.remove(nums[i - k]);
            }
        }
        return false;
    }
}
```