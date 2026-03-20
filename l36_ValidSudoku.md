# 36. Valid Sudoku

**LeetCode Problem:** [Valid Sudoku](https://leetcode.com/problems/valid-sudoku/)

## Approach
The approach to solving the "Valid Sudoku" problem involves iterating over the Sudoku board and checking each cell for validity. This is achieved by utilizing a HashSet to store unique strings representing the numbers in each row, column, and submatrix.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Initialize a HashSet called `seen` to store unique strings representing the numbers in each row, column, and submatrix.
2. **Step 2**: Iterate over each cell in the Sudoku board using nested loops for rows and columns.
3. **Step 3**: For each cell, check if the cell contains a number (i.e., not a '.').
4. **Step 4**: If the cell contains a number, create strings representing the number in the current row, column, and submatrix, and attempt to add them to the `seen` HashSet.
5. **Step 5**: If any of the strings cannot be added to the `seen` HashSet (i.e., they already exist), return false, indicating that the Sudoku board is not valid.
6. **Step 6**: If all cells have been checked and no duplicates were found, return true, indicating that the Sudoku board is valid.

- **Time Complexity**: The time complexity of this solution is O(1), as the size of the Sudoku board is fixed (9x9). However, in terms of the number of cells, it can be expressed as O(n^2), where n is the number of cells in one dimension (n = 9).
- **Space Complexity**: The space complexity of this solution is also O(1), as the maximum number of unique strings stored in the `seen` HashSet is constant (at most 81 cells * 3 checks per cell = 243 checks, but due to duplicates, it's less).

## Dry Run

Let's consider the following example input:
```markdown
[
  ["5","3",".",".","7",".",".",".","."],
  ["6",".",".","1","9","5",".",".","."],
  [".","9","8",".",".",".",".","6","."],
  ["8",".",".",".","6",".",".",".","3"],
  ["4",".",".","8",".","3",".",".","1"],
  ["7",".",".",".","2",".",".",".","6"],
  [".","6",".",".",".",".","2","8","."],
  [".",".",".","4","1","9",".",".","5"],
  [".",".",".",".","8",".",".","7","9"]
]
```
Here's the execution in a structured table format:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `seen` = {} | Initialize `seen` HashSet | `seen` = {} |
| 2 | `i` = 0, `j` = 0 | Start iterating over the board | `number` = '5' |
| 3 | `number` = '5' | Check if `number` is not '.' | `number` is not '.' |
| 4 | `number` = '5', `i` = 0, `j` = 0 | Attempt to add strings to `seen` | `seen` = {'5in rows0', '5in column0', '5in submatrix0-0'} |
| 5 | Continue iterating... | ... | ... |
| ... | ... | ... | ... |
| 81 | `i` = 8, `j` = 8 | Finish iterating over the board | `seen` contains all unique strings |
| - | `seen` contains all unique strings | Return true if no duplicates were found | Output: true |

Note that the table only shows a few key steps, as the full execution would involve 81 steps (one for each cell in the Sudoku board).
## Code
```java
class Solution {
    public boolean isValidSudoku(char[][] board) {
        HashSet<String> seen = new HashSet<>();

        for(int i = 0; i<9; i++){
            for(int j = 0; j<9; j++){
                char number = board[i][j];
                if(number != '.'){
                    if(!seen.add(number + "in rows" + i) ||
                        !seen.add(number + "in column" + j) ||
                        !seen.add(number + "in submatrix" + i/3 + "-" + j/3)){
                        return false;
                    }
                }

            }
        }

        return true;
    }
}
```