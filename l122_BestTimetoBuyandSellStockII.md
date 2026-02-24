# 122. Best Time to Buy and Sell Stock II

**LeetCode Problem:** [Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)

## Approach
The approach to solving the "Best Time to Buy and Sell Stock II" problem involves iterating through the array of stock prices and accumulating the difference in price whenever the current price is greater than the previous price. This greedy approach takes advantage of every opportunity to make a profit.

Here is a step-by-step breakdown:
1. **Step 1**: Initialize a variable `profit` to 0, which will store the total maximum profit that can be achieved.
2. **Step 2**: Iterate through the array of stock prices, starting from the second price (at index 1).
3. **Step 3**: For each price, check if it is greater than the previous price.
4. **Step 4**: If the current price is greater than the previous price, add the difference in price to the `profit` variable.
5. **Step 5**: Continue iterating through the array until all prices have been considered.
6. **Step 6**: Return the total `profit` as the result.

- **Time Complexity**: The time complexity of this algorithm is O(n), where n is the number of days (i.e., the length of the `prices` array), because we make a single pass through the array.
- **Space Complexity**: The space complexity of this algorithm is O(1), because we only use a constant amount of space to store the `profit` variable, regardless of the size of the input.

## Dry Run
Let's consider an example input: `prices = [7, 1, 5, 3, 6, 4]`.

Here's the execution in a structured table format:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `profit = 0`, `i = 1` | Compare `prices[1]` and `prices[0]` | `prices[1]` (1) is less than `prices[0]` (7), so do nothing |
| 2 | `profit = 0`, `i = 2` | Compare `prices[2]` and `prices[1]` | `prices[2]` (5) is greater than `prices[1]` (1), so add 4 to `profit` | `profit = 4` |
| 3 | `profit = 4`, `i = 3` | Compare `prices[3]` and `prices[2]` | `prices[3]` (3) is less than `prices[2]` (5), so do nothing | `profit = 4` |
| 4 | `profit = 4`, `i = 4` | Compare `prices[4]` and `prices[3]` | `prices[4]` (6) is greater than `prices[3]` (3), so add 3 to `profit` | `profit = 7` |
| 5 | `profit = 7`, `i = 5` | Compare `prices[5]` and `prices[4]` | `prices[5]` (4) is less than `prices[4]` (6), so do nothing | `profit = 7` |
| 6 | `profit = 7` | Return `profit` |  | `profit = 7` |

The final result is a maximum profit of 7.
## Code
```java
class Solution {
    public int maxProfit(int[] prices) {
        int profit = 0;

        for(int i =1; i<prices.length; i++){
            if(prices[i] > prices[i-1]){
                profit+=prices[i] - prices[i-1];
            }
        }

        return profit;
    }
}
```