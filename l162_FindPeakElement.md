# 162. Find Peak Element

**LeetCode Problem:** [Find Peak Element](https://leetcode.com/problems/find-peak-element/)

## Approach
Use a binary‑search‑style technique that repeatedly compares an element with its right neighbor. If the current element is smaller than the next one, a peak must exist on the right side; otherwise, a peak lies on the left side (including the current element). Shrink the search interval until `left == right`; that index is a peak.

### Step‑by‑step breakdown
1. **Initialize pointers** – `left` points to the first index (`0`) and `right` points to the last index (`nums.length‑1`).  
2. **Loop while the search window has more than one element** (`left < right`).  
3. **Compute middle index** – `mid = left + (right‑left)/2` to avoid overflow.  
4. **Compare `nums[mid]` with its right neighbor `nums[mid+1]`**  
   - If `nums[mid] < nums[mid+1]`, the slope is upward, so a peak must be to the right of `mid`. Move `left` to `mid + 1`.  
   - Otherwise (`nums[mid] >= nums[mid+1]`), the slope is downward or flat, meaning a peak is at `mid` or to its left. Move `right` to `mid`.  
5. **When the loop ends**, `left` and `right` converge to the same index, which is a peak. Return that index.

- **Time Complexity**: `O(log n)` – each iteration halves the search interval.  
- **Space Complexity**: `O(1)` – only a few integer variables are used regardless of input size.

---

## Dry Run  

**Example input:** `nums = [1, 2, 3, 1]`  

| Step | `left` | `right` | `mid` (computed) | Action taken                                 | New `left` / `right` |
|------|--------|---------|------------------|----------------------------------------------|----------------------|
| 1    | 0      | 3       | 1 (`0 + (3‑0)/2`) | `nums[1] = 2` < `nums[2] = 3` → move right | `left = 2`           |
| 2    | 2      | 3       | 2 (`2 + (3‑2)/2`) | `nums[2] = 3` ≥ `nums[3] = 1` → move left   | `right = 2`          |
| 3    | 2      | 2       | –                | Loop condition `left < right` fails        | –                    |

The loop terminates with `left = 2`. Index 2 holds the value `3`, which is a peak (greater than its neighbors). The algorithm returns `2`.
## Code
```java
class Solution {
    public int findPeakElement(int[] nums) {
        int left = 0;
        int right = nums.length - 1;

        while (left < right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] < nums[mid + 1]) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        return left;
    }
}
```