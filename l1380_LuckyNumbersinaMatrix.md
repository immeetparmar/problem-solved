# 1380. Lucky Numbers in a Matrix

**LeetCode Problem:** [Lucky Numbers in a Matrix](https://leetcode.com/problems/lucky-numbers-in-a-matrix/)

## Approach
The approach used to solve the "Lucky Numbers in a Matrix" problem involves finding the minimum element in each row and the maximum element in each column, then identifying the common elements between these two sets. This is done by iterating through the matrix to find the minimum and maximum values, and then comparing these values to find the lucky numbers.

Here is a step-by-step breakdown of the logic:
1. **Step 1**: Find the minimum element in each row of the matrix and store these values in a list (`minRow`).
2. **Step 2**: Find the maximum element in each column of the matrix and store these values in a list (`maxCol`).
3. **Step 3**: Iterate through the matrix again to find the elements that are both the minimum of their row and the maximum of their column, and add these elements to the result list (`result`).

- **Time Complexity**: The time complexity of this solution is O(m*n), where m is the number of rows and n is the number of columns in the matrix. This is because we are iterating through the matrix three times: once to find the minimum of each row, once to find the maximum of each column, and once to find the lucky numbers.
- **Space Complexity**: The space complexity of this solution is O(m + n), where m is the number of rows and n is the number of columns in the matrix. This is because we are storing the minimum of each row and the maximum of each column in separate lists.

## Dry Run
Let's use the following example input to demonstrate the algorithm:
```markdown
Input matrix:
[
  [3, 7, 8],
  [9, 11, 13],
  [15, 16, 17]
]
```
Here is the execution of the algorithm in a structured table format:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `minRow = []`, `maxCol = []`, `result = []` | Find minimum of each row | `minRow = [3, 9, 15]` |
| 2 | `minRow = [3, 9, 15]`, `maxCol = []`, `result = []` | Find maximum of each column | `maxCol = [15, 16, 17]` |
| 3 | `minRow = [3, 9, 15]`, `maxCol = [15, 16, 17]`, `result = []` | Find lucky numbers | `result = [15]` |

The final output of the algorithm is `[15]`, which is the lucky number in the input matrix.
## Code
```java
class Solution {
    public List<Integer> luckyNumbers(int[][] matrix) {
        

        int m = matrix.length;
        int n = matrix[0].length;
        ArrayList<Integer> minRow = new ArrayList<>();
        ArrayList<Integer> maxCol = new ArrayList<>();

        // list is an interface
        // ArrayList is a class. 

        ArrayList<Integer> result = new ArrayList<>();

// finding min elem in every row
        for(int i=0; i<m; i++) {
            int minElm = Integer.MAX_VALUE;
            for(int j=0; j<n; j++) {
                minElm = Math.min(minElm, matrix[i][j]);
            }
            minRow.add(minElm);
        }
// finding max elem in every col
        for(int j=0; j<n; j++) {
            int maxElm = Integer.MIN_VALUE;
            for(int i=0; i<m; i++) {
                maxElm = Math.max(maxElm, matrix[i][j]);
            }
            maxCol.add(maxElm);
        }


        // now we have to find common value in maxCol a and minRow
        for(int i=0; i<m; i++) {
            for(int j=0; j<n; j++) {
                if(matrix[i][j] == minRow.get(i) && matrix[i][j] == maxCol.get(j)) {
                    result.add(matrix[i][j]);
                }
            }
        }
        return result;
    }
}

```