# 977. Squares of a Sorted Array

**LeetCode Problem:** [Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/)

## Approach  
Use two pointers that start at the opposite ends of the sorted array. Because the largest absolute value (and therefore the largest square) must be at one of the ends, we compare the absolute values, place the larger square at the current highest free position in the answer array, and move the corresponding pointer inward. Continue until the whole answer array is filled.

### Step‑by‑step breakdown  

1. **Initialize**  
   * `l = 0` (left pointer)  
   * `r = n‑1` (right pointer)  
   * `index = n‑1` (position to fill in the result array)  

2. **Compare absolute values**  
   * While `l <= r`, compare `|nums[l]|` and `|nums[r]|`.  

3. **Place the larger square**  
   * If `|nums[l]| > |nums[r]|` → `ans[index] = nums[l] * nums[l]` and move `l` right (`l++`).  
   * Otherwise → `ans[index] = nums[r] * nums[r]` and move `r` left (`r--`).  

4. **Move the fill index**  
   * After each placement, decrement `index` (`index--`).  

5. **Terminate**  
   * Loop ends when `l > r`. The `ans` array now contains the squares in non‑decreasing order.  

---

- **Time Complexity**: **O(n)** – each element is inspected exactly once.  
- **Space Complexity**: **O(n)** – an extra array of size `n` is allocated for the result.

## Dry Run  

**Input:** `[-4, -1, 0, 3, 10]`  

| Step | `l` | `r` | `index` | `ans` (filled positions) | Action | Result / Updated Variables |
|------|-----|-----|---------|--------------------------|--------|-----------------------------|
| 0 (init) | 0 | 4 | 4 | `[_, _, _, _, _]` | – | `l=0, r=4, index=4` |
| 1 | 0 | 4 | 4 | `[_, _, _, _, _]` | Compare `|‑4|=4` vs `|10|=10` → right larger | `ans[4]=10*10=100`, `r=3`, `index=3` |
| 2 | 0 | 3 | 3 | `[_, _, _, _, 100]` | Compare `|‑4|=4` vs `|3|=3` → left larger | `ans[3]=(-4)*(-4)=16`, `l=1`, `index=2` |
| 3 | 1 | 3 | 2 | `[_, _, _, 16, 100]` | Compare `|‑1|=1` vs `|3|=3` → right larger | `ans[2]=3*3=9`, `r=2`, `index=1` |
| 4 | 1 | 2 | 1 | `[_, _, 9, 16, 100]` | Compare `|‑1|=1` vs `|0|=0` → left larger | `ans[1]=(-1)*(-1)=1`, `l=2`, `index=0` |
| 5 | 2 | 2 | 0 | `[_, 1, 9, 16, 100]` | Compare `|0|=0` vs `|0|=0` (equal, take right) | `ans[0]=0*0=0`, `r=1`, `index=-1` |
| 6 | 2 | 1 | -1 | `[0, 1, 9, 16, 100]` | Loop condition `l <= r` fails (`2 > 1`) | Terminate |

**Final output:** `[0, 1, 9, 16, 100]` – the squares of the original sorted array, also sorted.
## Code
```java
// class Solution {
//     public int[] sortedSquares(int[] nums) {

//         for (int i = 0; i < nums.length; i++) {
//             nums[i] = nums[i] * nums[i];
//         }
//         Arrays.sort(nums);
//         return nums;
//     }
// }
// 
class Solution {
    public int[] sortedSquares(int[] nums) {
        int n = nums.length;
        int[] ans = new int[n];

        int l = 0;
        int r = n - 1;
        int index = n - 1;

        while (l <= r) {
            if (Math.abs(nums[l]) > Math.abs(nums[r])) {
                ans[index] = nums[l] * nums[l];
                l++;
            } else {
                ans[index] = nums[r] * nums[r];
                r--;
            }
            index--;
        }
        return ans;
    }
}
```