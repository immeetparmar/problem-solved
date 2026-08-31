# 852. Peak Index in a Mountain Array

**LeetCode Problem:** [Peak Index in a Mountain Array](https://leetcode.com/problems/peak-index-in-a-mountain-array/)

## Approach  

Use binary search to locate the peak of the mountain array.  
At each iteration compare the middle element with its right neighbour: if the middle element is smaller, the peak lies to the right; otherwise it lies at the middle or to the left. The loop converges to the index of the maximum element.

### Step‑by‑step breakdown  

1. **Initialize pointers** – `left` points to the first index (`0`) and `right` points to the last index (`arr.length‑1`).  
2. **Iterate while `left < right`** – keep narrowing the search interval until the two pointers meet.  
3. **Compute middle index** – `mid = left + (right‑left)/2` to avoid overflow.  
4. **Compare `arr[mid]` with `arr[mid+1]`**  
   * If `arr[mid] < arr[mid+1]`, the slope is ascending, so the peak must be **right** of `mid`. Set `left = mid + 1`.  
   * Otherwise the slope is descending (or we are at the peak), so the peak is **at** `mid` or to its left. Set `right = mid`.  
5. **Loop ends** – when `left == right`, both pointers indicate the peak index.  
6. **Return the peak index** – the value of `left` (or `right`).  

---

### Complexity  

- **Time Complexity:** `O(log n)` – each iteration halves the search interval.  
- **Space Complexity:** `O(1)` – only a few integer variables are used regardless of input size.  

---

## Dry Run  

**Example input:** `arr = [1, 3, 5, 4, 2]`  

| Step | `left` | `right` | `mid` | `arr[mid]` | `arr[mid+1]` | Condition (`arr[mid] < arr[mid+1]`?) | Action                | New `left` / `right` |
|------|--------|---------|------|------------|--------------|--------------------------------------|-----------------------|----------------------|
| 1    | 0      | 4       | 2    | 5          | 4            | **false**                           | `right = mid`        | `left=0`, `right=2` |
| 2    | 0      | 2       | 1    | 3          | 5            | **true**                            | `left = mid + 1`     | `left=2`, `right=2` |
| 3    | 2      | 2       | –    | –          | –            | loop condition fails (`left == right`) | exit loop            | –                    |

**Result:** The algorithm returns `left = 2`, which is the index of the peak element `5`. The dry run shows how the search interval shrinks until it converges on the correct peak.
## Code
```java
public class Solution {
    public int peakIndexInMountainArray(int[] arr) {
        int left = 0;
        int right = arr.length - 1;

        while (left < right) {
            int mid = left + (right - left) / 2;

            if (arr[mid] < arr[mid + 1]) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        return left;
    }
}
```