# 577. Employee Bonus

**LeetCode Problem:** [Employee Bonus](https://leetcode.com/problems/employee-bonus/)

## Approach
The approach involves a simple SQL query that joins the Employee and Bonus tables based on the empId, and then selects the name and bonus for employees who either do not have a bonus or have a bonus less than 1000. This is achieved through a LEFT JOIN and a WHERE clause.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: The query starts by selecting the name from the Employee table and the bonus from the Bonus table.
2. **Step 2**: It then performs a LEFT JOIN on the Employee and Bonus tables based on the empId, which means all records from the Employee table are included, and matching records from the Bonus table are added if available.
3. **Step 3**: The query applies a WHERE clause to filter the results, only including rows where the bonus is less than 1000 or where the bonus is NULL (i.e., the employee does not have a bonus).
4. **Step 4**: The final result is the list of employee names along with their corresponding bonuses, if any, that meet the specified conditions.

- **Time Complexity**: The time complexity of this query is O(n), where n is the total number of rows in the Employee table, since in the worst case, the query has to scan all rows in the Employee table.
- **Space Complexity**: The space complexity is also O(n), as the query needs to store the results of the join operation, which can be as large as the number of rows in the Employee table.

## Dry Run

Let's consider an example where we have the following data:

Employee table:
| empId | name |
|-------|------|
| 1     | John |
| 2     | Jane |
| 3     | Joe  |

Bonus table:
| empId | bonus |
|-------|-------|
| 1     | 500   |
| 2     | 1500  |

Here's how the query would execute:

| Step number | Current state of variables | Action taken | Result/Output |
|-------------|----------------------------|--------------|----------------|
| 1           | Employee and Bonus tables   | Perform LEFT JOIN on empId | Joined table with all Employee rows and matching Bonus rows |
| 2           | Joined table               | Apply WHERE clause (bonus < 1000 OR bonus IS NULL) | Filtered table with John and Joe |
| 3           | Filtered table             | Select name and bonus | John, 500; Joe, NULL |

The final result would be:
| name | bonus |
|------|-------|
| John | 500   |
| Joe  | NULL  |
## Code
```mysql
SELECT e.name, b.bonus
FROM Employee e
LEFT JOIN Bonus b
ON e.empId = b.empId
WHERE b.bonus < 1000 OR b.bonus IS NULL;

```