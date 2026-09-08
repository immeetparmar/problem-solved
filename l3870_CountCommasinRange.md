# 3870. Count Commas in Range

**LeetCode Problem:** [Count Commas in Range](https://leetcode.com/problems/count-commas-in-range/)

## Approach  
The algorithm computes how many commas would appear when writing all integers from 1 to `n` in decimal notation. A comma is inserted after every three digits, so numbers 1‑999 contain no commas. Starting from 1000, each additional number adds exactly one comma. Therefore, the answer is simply `max(0, n‑999)`.

### Step‑by‑step breakdown
1. **Step 1 – Input received**: The method receives the integer `n`.  
2. **Step 2 – Compute raw count**: Calculate `n - 999`. This yields the number of integers that are ≥ 1000.  
3. **Step 3 – Clamp to non‑negative**: Apply `Math.max(0, …)` so that for `n < 1000` the result becomes 0 (no commas).  
4. **Step 4 – Return result**: The final value is returned as the count of commas.

---

- **Time Complexity**: **O(1)** – only a constant number of arithmetic operations are performed.  
- **Space Complexity**: **O(1)** – no additional data structures are allocated; only a few primitive variables are used.

## Dry Run  

**Example input:** `n = 1500`

| Step | Variables (`n`, intermediate) | Action taken                                 | Result / Output |
|------|-------------------------------|----------------------------------------------|-----------------|
| 1    | `n = 1500`                    | Receive input                                 | – |
| 2    | compute `1500 - 999 = 501`    | Subtract 999 from `n`                         | intermediate = 501 |
| 3    | `Math.max(0, 501)`            | Clamp to non‑negative                         | final = 501 |
| 4    | –                             | Return the final value                        | **501** commas |

The dry run shows that for all numbers from 1 to 1500, the numbers 1000‑1500 each contribute one comma, giving a total of 501 commas.
## Code
```java
class Solution {
    public int countCommas(int n) {
        return Math.max(0, n - 999);
    }
}
```