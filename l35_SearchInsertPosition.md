# 35. Search Insert Position

**LeetCode Problem:** [Search Insert Position](https://leetcode.com/problems/search-insert-position/)

## Approach  
Use binary search to locate the target in the sorted array. While narrowing the search interval, keep track of the left boundary; when the loop ends, `left` is the correct insertion index (or the index of the target if it exists).

### Step‑by‑step breakdown
1. **Initialize pointers** – `left` points to the start of the array (`0`) and `right` points to the last index (`nums.length‑1`).  
2. **Loop condition** – Continue while `left <= right`. This ensures the search interval is valid.  
3. **Compute middle** – `mid = left + (right‑left)/2` avoids overflow and picks the middle index of the current interval.  
4. **Check equality** –  
   * If `nums[mid] == target`, the target is found; return `mid`.  
5. **Target larger than middle** –  
   * If `nums[mid] < target`, discard the left half by setting `left = mid + 1`.  
6. **Target smaller than middle** –  
   * Otherwise (`nums[mid] > target`), discard the right half by setting `right = mid - 1`.  
7. **Loop ends** – When `left > right`, the target is not present. The current value of `left` is the smallest index where `target` could be inserted while preserving order. Return `left`.

---

- **Time Complexity**: `O(log n)` – each iteration halves the search interval.  
- **Space Complexity**: `O(1)` – only a few integer variables are used, independent of input size.

## Dry Run  

**Example:** `nums = [1, 3, 5, 6]`, `target = 2`  

| Step | `left` | `right` | `mid` | `nums[mid]` | Action                               | Result (`left`, `right`) |
|------|--------|---------|------|-------------|--------------------------------------|--------------------------|
| 1    | 0      | 3       | 1    | 3           | `nums[mid] > target` → move `right` | `left=0`, `right=0`      |
| 2    | 0      | 0       | 0    | 1           | `nums[mid] < target` → move `left`  | `left=1`, `right=0`      |
| 3    | 1      | 0       | –    | –           | Loop condition fails (`left > right`) | Return `left = 1`       |

**Explanation:**  
- After the first iteration, the algorithm discards the right half because `3 > 2`.  
- In the second iteration, it discards the left half because `1 < 2`.  
- The loop ends with `left = 1`, which is the correct insertion position for `2` in the sorted array.
## Code
```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int left = 0, right = nums.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (nums[mid] == target)
                return mid;
            else if (nums[mid] < target)
                left = mid + 1;
            else
                right = mid - 1;
        }

        return left;
    }
}
```