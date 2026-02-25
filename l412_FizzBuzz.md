# 412. Fizz Buzz

**LeetCode Problem:** [Fizz Buzz](https://leetcode.com/problems/fizz-buzz/)

## Approach
The approach to solving the "Fizz Buzz" problem involves iterating through numbers from 1 to n and checking each number for divisibility by 3 and 5. The algorithm then appends the corresponding string ("Fizz", "Buzz", "FizzBuzz", or the number itself) to the result list.

Here is a step-by-step breakdown of the logic:
1. **Step 1**: Initialize an empty list to store the results.
2. **Step 2**: Iterate through numbers from 1 to n (inclusive) using a for loop.
3. **Step 3**: For each number, check if it is divisible by both 3 and 5. If true, append "FizzBuzz" to the result list.
4. **Step 4**: If the number is not divisible by both, check if it is divisible by 3. If true, append "Fizz" to the result list.
5. **Step 5**: If the number is not divisible by 3, check if it is divisible by 5. If true, append "Buzz" to the result list.
6. **Step 6**: If the number is not divisible by either 3 or 5, append the number itself (as a string) to the result list.
7. **Step 7**: After iterating through all numbers, return the result list.

- **Time Complexity**: The time complexity of this solution is O(n), where n is the input number, because it involves a single loop that runs from 1 to n.
- **Space Complexity**: The space complexity is also O(n), as in the worst-case scenario, the result list will contain n elements (when none of the numbers are divisible by 3 or 5).

## Dry Run
Let's take n = 5 as an example input. Here's the step-by-step execution:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | i = 1, al = [] | Initialize list | al = [] |
| 2 | i = 1, al = [] | Check divisibility, append "1" | al = ["1"] |
| 3 | i = 2, al = ["1"] | Check divisibility, append "2" | al = ["1", "2"] |
| 4 | i = 3, al = ["1", "2"] | Check divisibility, append "Fizz" | al = ["1", "2", "Fizz"] |
| 5 | i = 4, al = ["1", "2", "Fizz"] | Check divisibility, append "4" | al = ["1", "2", "Fizz", "4"] |
| 6 | i = 5, al = ["1", "2", "Fizz", "4"] | Check divisibility, append "Buzz" | al = ["1", "2", "Fizz", "4", "Buzz"] |

The final output will be `["1", "2", "Fizz", "4", "Buzz"]`.
## Code
```java
class Solution {
    public List<String> fizzBuzz(int n) {
        
        ArrayList<String> al = new ArrayList<>();

        for (int i = 1; i <= n; i++) {
            if (i % 3 == 0 && i % 5 == 0) {
                al.add("FizzBuzz");
            } else if (i % 3 == 0) {
                al.add("Fizz");
            } else if (i % 5 == 0) {
                al.add("Buzz");
            } else {
                al.add(String.valueOf(i));
            }
        }

        return al;


    }
}
```