# 704. Binary Search

**LeetCode Problem:** [Binary Search](https://leetcode.com/problems/binary-search/)

## Approach  

Use classic binary search: repeatedly halve the sorted interval until the target is found or the interval becomes empty.

### Step‑by‑step breakdown  

1. **Initialize pointers** – `left` points to the first index (`0`) and `right` points to the last index (`n‑1`).  
2. **Loop condition** – Continue while `left ≤ right`. This means there is still a searchable sub‑array.  
3. **Compute middle** – `mid = left + (right‑left)/2`. The formula avoids overflow.  
4. **Check middle element** –  
   * If `nums[mid] == target`, return `mid` – the target is found.  
   * If `nums[mid] < target`, the target can only be in the right half, so set `left = mid + 1`.  
   * Otherwise (`nums[mid] > target`), the target can only be in the left half, so set `right = mid - 1`.  
5. **Repeat** – Go back to step 2 with the updated `left` and `right`.  
6. **Not found** – If the loop exits, the target is absent; return `-1`.

---

- **Time Complexity**: `O(log n)` – each iteration cuts the search interval in half.  
- **Space Complexity**: `O(1)` – only a few integer variables are used, regardless of input size.

## Dry Run  

**Example:** `nums = [1, 3, 5, 7, 9]`, `target = 7`

| Step | `left` | `right` | `mid` | `nums[mid]` | Action taken | Result (`left`, `right`, return`) |
|------|--------|---------|------|------------|--------------|-----------------------------------|
| 1    | 0      | 4       | 2    | 5          | `5 < 7` → search right half | `left = 3`, `right = 4` |
| 2    | 3      | 4       | 3    | 7          | `nums[mid] == target` → return index | Return **3** (search ends) |

The algorithm finds the target at index 3 after just two iterations, illustrating the logarithmic reduction of the search space.
## Code
```java
class Solution {
    public int search(int[] nums, int target) {
        int n = nums.length;
        int left = 0;
        int right = n - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (nums[mid] == target) {
                return mid;
            } else if (nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return -1;
    }
}
```