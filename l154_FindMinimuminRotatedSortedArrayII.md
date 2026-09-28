# 154. Find Minimum in Rotated Sorted Array II

**LeetCode Problem:** [Find Minimum in Rotated Sorted Array II](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/)

## Approach  

The algorithm uses a modified binary search to locate the smallest element in a rotated sorted array that may contain duplicates. By comparing the middle element with the rightmost element we can decide which half still contains the minimum; when they are equal we safely shrink the search interval by moving `right` one step left.

### Step‑by‑step breakdown  

1. **Initialize pointers** – `left` points to the first index (0) and `right` points to the last index (`nums.length‑1`).  
2. **Loop condition** – Continue while `left < right`; when they meet the minimum has been found.  
3. **Compute mid** – `mid = left + (right‑left)/2` to avoid overflow.  
4. **Compare `nums[mid]` with `nums[right]`**  
   - **If `nums[mid] > nums[right]`** → the minimum must be to the right of `mid`; set `left = mid + 1`.  
   - **If `nums[mid] < nums[right]`** → the minimum lies at `mid` or to its left; set `right = mid`.  
   - **If `nums[mid] == nums[right]`** → we cannot tell which side contains the minimum, but we can safely discard `right` because `nums[right]` is a duplicate of `nums[mid]`; do `right--`.  
5. **Repeat** – Go back to step 2 with the updated pointers.  
6. **Return result** – When the loop exits, `left == right`; `nums[left]` (or `nums[right]`) is the smallest value.

---

### Complexity  

- **Time Complexity**: `O(log n)` in the average case (when duplicates are rare). In the worst case (e.g., all elements equal) the algorithm degrades to `O(n)` because the `right--` step may be executed for every element.  
- **Space Complexity**: `O(1)` – only a few integer variables are used, independent of the input size.

---

## Dry Run  

**Example input**: `nums = [2, 2, 2, 0, 1]`

| Step | `left` | `right` | `mid` | `nums[mid]` | `nums[right]` | Action taken | New `left` / `right` |
|------|--------|---------|------|-------------|---------------|--------------|----------------------|
| 1    | 0      | 4       | 2    | 2           | 1             | `nums[mid] > nums[right]` → move left to `mid+1` | `left = 3`, `right = 4` |
| 2    | 3      | 4       | 3    | 0           | 1             | `nums[mid] < nums[right]` → move right to `mid` | `left = 3`, `right = 3` |
| 3    | 3      | 3       | –    | –           | –             | Loop condition fails (`left == right`) | – |
| 4    | –      | –       | –    | –           | –             | Return `nums[left]` | Result = **0** |

The algorithm correctly identifies **0** as the minimum element.
## Code
```java
class Solution {
    public int findMin(int[] nums) {

        int left = 0;
        int right = nums.length - 1;

        while (left < right) {

            int mid = left + (right - left) / 2;

            if (nums[mid] > nums[right]) {
                left = mid + 1;
            }
            else if (nums[mid] < nums[right]) {
                right = mid;
            }
            else {
                right--;
            }
        }

        return nums[left];
    }
}
```