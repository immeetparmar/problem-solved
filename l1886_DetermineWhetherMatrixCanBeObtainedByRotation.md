# 1886. Determine Whether Matrix Can Be Obtained By Rotation

**LeetCode Problem:** [Determine Whether Matrix Can Be Obtained By Rotation](https://leetcode.com/problems/determine-whether-matrix-can-be-obtained-by-rotation/)

## Approach

The approach to solving this problem involves checking if the target matrix can be obtained by rotating the given matrix by 0, 90, 180, or 270 degrees. This is achieved by implementing a rotation function and comparing the resulting matrices with the target matrix.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Initialize a counter to keep track of the number of rotations, and set the initial matrix to the given matrix.
2. **Step 2**: Check if the current matrix is equal to the target matrix. If they are equal, return true.
3. **Step 3**: If the matrices are not equal, rotate the current matrix by 90 degrees.
4. **Step 4**: Repeat steps 2 and 3 for a total of 4 rotations (0, 90, 180, and 270 degrees).
5. **Step 5**: If none of the rotations result in a match with the target matrix, return false.

- **Time Complexity**: The time complexity of this algorithm is O(n^2 * 4), where n is the number of rows (or columns) in the matrix. This simplifies to O(n^2) because constant factors are ignored in Big O notation.
- **Space Complexity**: The space complexity is O(n^2) due to the creation of a new matrix during each rotation.

## Dry Run

Let's use the following example input:
- `mat = [[0,1],[1,1]]`
- `target = [[1,0],[1,1]]`

Here's the step-by-step execution:

| Step Number | Current State of Variables | Action Taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `mat = [[0,1],[1,1]]`, `target = [[1,0],[1,1]]`, `rotation = 0` | Compare `mat` with `target` | `mat` and `target` are not equal |
| 2 | `mat = [[0,1],[1,1]]`, `target = [[1,0],[1,1]]`, `rotation = 0` | Rotate `mat` by 90 degrees | `mat` becomes `[[1,0],[1,1]]` |
| 3 | `mat = [[1,0],[1,1]]`, `target = [[1,0],[1,1]]`, `rotation = 1` | Compare `mat` with `target` | `mat` and `target` are equal, return `true` |

The algorithm returns `true` after the first rotation, indicating that the target matrix can be obtained by rotating the given matrix.
## Code
```java
class Solution {
    public boolean findRotation(int[][] mat, int[][] target) {

        int n = mat.length;

        for(int i=0; i<4; i++){
            if(isEqual(mat, target)){
                return true;
            }
            mat = rotate(mat);
        }

        return false;
    }

    public boolean isEqual(int[][] arr1, int[][] arr2){
        int n = arr1.length, m = arr1[0].length;
         for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if (arr1[i][j] != arr2[i][j]) {
                    return false;
                }
            }
        }
        return true;
    }
    
    public int[][] rotate(int[][] arr) {
        int n = arr.length;
        int m = arr[0].length;
        int[][] res = new int[m][n];

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                res[j][n - i - 1] = arr[i][j];
            }
        }
        return res;
    }
}
```