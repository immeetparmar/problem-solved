# 121. Best Time to Buy and Sell Stock

**LeetCode Problem:** [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

## Approach
The approach to solving the "Best Time to Buy and Sell Stock" problem involves iterating through the list of prices to find the maximum possible profit by keeping track of the minimum price encountered so far and the maximum profit that can be achieved. This is done in a single pass through the prices array, making it an efficient solution.

Here's a step-by-step breakdown of the logic:
1. **Initialization**: Initialize two variables, `min` and `profit`, to keep track of the minimum price encountered and the maximum possible profit, respectively. `min` is set to `Integer.MAX_VALUE` to ensure the first price encountered will be less than it, and `profit` is set to 0, assuming no profit initially.
2. **Iteration**: Iterate through each price in the `prices` array. For each price, check if it's less than the current `min` value. If it is, update `min` to this new price, as this could potentially lead to a higher profit if sold at a later higher price.
3. **Profit Update**: If the current price is not less than `min`, calculate the potential profit by subtracting `min` from the current price. Update `profit` with the maximum of its current value and this calculated potential profit. This ensures `profit` always holds the maximum possible profit found so far.
4. **Result**: After iterating through all prices, `profit` will hold the maximum possible profit that can be achieved by buying and selling the stock once, based on the given prices.

- **Time Complexity**: The time complexity of this solution is O(n), where n is the number of elements in the `prices` array, because it involves a single pass through the array.
- **Space Complexity**: The space complexity is O(1), meaning the space required does not change with the size of the input array, as only a constant amount of space is used to store the `min` and `profit` variables.

## Dry Run
Let's consider the input `prices = [7,1,5,3,6,4]` as an example to demonstrate the algorithm's execution.

| Step Number | Current State of Variables | Action Taken | Result/Output |
|-------------|----------------------------|--------------|---------------|
| 1           | min = Integer.MAX_VALUE, profit = 0 | Initialize variables | min = 2147483647, profit = 0 |
| 2           | min = 2147483647, profit = 0 | price = 7, update min to 7 | min = 7, profit = 0 |
| 3           | min = 7, profit = 0 | price = 1, update min to 1 | min = 1, profit = 0 |
| 4           | min = 1, profit = 0 | price = 5, calculate profit = 5 - 1 = 4, update profit | min = 1, profit = 4 |
| 5           | min = 1, profit = 4 | price = 3, no update | min = 1, profit = 4 |
| 6           | min = 1, profit = 4 | price = 6, calculate profit = 6 - 1 = 5, update profit | min = 1, profit = 5 |
| 7           | min = 1, profit = 5 | price = 4, no update | min = 1, profit = 5 |
| 8           | min = 1, profit = 5 | End of iteration | Final profit = 5 |

The final output of the algorithm for the input `prices = [7,1,5,3,6,4]` is `5`, indicating the maximum possible profit that can be achieved is by buying the stock at price `1` and selling it at price `6`.
## Code
```java
class Solution {
    public int maxProfit(int[] prices) {
        int min = Integer.MAX_VALUE;
        int profit = 0;

        for(int price : prices){
            if(price < min){
                 min = price;
            }
            else profit = Math.max(profit, price - min);
        }
        return profit;
    }
}
```