# 74. Search a 2D Matrix

**LeetCode Problem:** [Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/)

## Approach  

Treat the `m × n` matrix as a flattened sorted 1‑D array and perform a classic binary search on the index range `[0, m·n‑1]`.  
At each iteration convert the middle index back to a row and column to compare the element with the target.

### Step‑by‑step breakdown  

1. **Initialize dimensions** – Compute `m` (number of rows) and `n` (number of columns).  
2. **Set binary‑search bounds** – `left = 0`, `right = m·n ‑ 1`.  
3. **Loop while the search window is valid** (`left ≤ right`).  
4. **Pick the middle index** – `mid = left + (right‑left)/2`.  
5. **Map `mid` to matrix coordinates** – `row = mid / n`, `col = mid % n`.  
6. **Compare the current element** `matrix[row][col]` with `target`.  
   * If equal → **return `true`** (target found).  
   * If smaller → move the left bound: `left = mid + 1`.  
   * If larger → move the right bound: `right = mid - 1`.  
7. **If the loop ends** without a match, **return `false`** (target not present).

---

### Complexity  

- **Time Complexity:** `O(log (m·n))` – binary search halves the search space each iteration.  
- **Space Complexity:** `O(1)` – only a few integer variables are used, independent of matrix size.

---

## Dry Run  

**Example:**  

```text
matrix = [
  [1, 3, 5, 7],
  [10,11,16,20],
  [23,30,34,50]
]
target = 3
```

`m = 3`, `n = 4`, so the virtual array length is `12`.

| Step | Variables (`left`, `right`, `mid`, `row`, `col`, `matrix[row][col]`) | Action | Result / Output |
|------|---------------------------------------------------------------------|--------|-----------------|
| 1    | left = 0, right = 11, mid = 5 (0 + (11‑0)/2)                         | Compute `row = 5/4 = 1`, `col = 5%4 = 1` | Current element = `matrix[1][1] = 11` |
| 2    | left = 0, right = 11, mid = 5, element = 11                         | 11 > target → move right bound | right = mid‑1 = 4 |
| 3    | left = 0, right = 4, mid = 2 (0 + (4‑0)/2)                           | Compute `row = 2/4 = 0`, `col = 2%4 = 2` | Current element = `matrix[0][2] = 5` |
| 4    | left = 0, right = 4, mid = 2, element = 5                          | 5 > target → move right bound | right = mid‑1 = 1 |
| 5    | left = 0, right = 1, mid = 0 (0 + (1‑0)/2)                           | Compute `row = 0/4 = 0`, `col = 0%4 = 0` | Current element = `matrix[0][0] = 1` |
| 6    | left = 0, right = 1, mid = 0, element = 1                          | 1 < target → move left bound | left = mid+1 = 1 |
| 7    | left = 1, right = 1, mid = 1 (1 + (1‑1)/2)                           | Compute `row = 1/4 = 0`, `col = 1%4 = 1` | Current element = `matrix[0][1] = 3` |
| 8    | left = 1, right = 1, mid = 1, element = 3                          | element == target → **return `true`** | Search finishes, target found |

The algorithm finds the target `3` after 8 logical steps, confirming its correctness.
## Code
```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int m = matrix.length;
        int n = matrix[0].length;

        int left = 0;
        int right = m * n - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;
            int row = mid / n;
            int col = mid % n;

            if (matrix[row][col] == target) {
                return true;
            } else if (matrix[row][col] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return false;
    }
}
```