# 9. Palindrome Number

**LeetCode Problem:** [Palindrome Number](https://leetcode.com/problems/palindrome-number/)

## Approach

The approach to solving the "Palindrome Number" problem involves checking if the input number is a palindrome by reversing half of the number and comparing it with the other half. This is done by continuously taking the last digit of the number, adding it to the reversed half, and removing it from the original number.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Check if the input number is negative or if it's a multiple of 10 (but not 0), in which case it's not a palindrome.
2. **Step 2**: Initialize a variable `reversedHalf` to store the reversed half of the number.
3. **Step 3**: Enter a while loop that continues until the original number is less than or equal to the reversed half.
4. **Step 4**: Inside the loop, extract the last digit of the original number using the modulo operator (`x % 10`), add it to the `reversedHalf` after shifting its current digits one place to the left (`reversedHalf * 10`), and remove the last digit from the original number (`x / 10`).
5. **Step 5**: Once the loop ends, check if the original number is equal to the reversed half or if the original number is equal to the reversed half divided by 10 (to handle cases where the original number has an odd number of digits).

- **Time Complexity**: The time complexity of this solution is O(log n), where n is the input number, since we're effectively processing each digit of the number once.
- **Space Complexity**: The space complexity is O(1), as we're only using a constant amount of space to store the variables `x` and `reversedHalf`, regardless of the input size.

## Dry Run

Let's take the input `x = 12321` as an example. Here's the step-by-step execution:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `x = 12321`, `reversedHalf = 0` | Check if `x` is negative or a multiple of 10 | Pass the check |
| 2 | `x = 12321`, `reversedHalf = 0` | Initialize `reversedHalf` | `reversedHalf` remains 0 |
| 3 | `x = 12321`, `reversedHalf = 0` | Enter while loop | Loop condition is true (`x > reversedHalf`) |
| 4 | `x = 12321`, `reversedHalf = 0` | Extract last digit (`1`), add to `reversedHalf`, remove from `x` | `x = 1232`, `reversedHalf = 1` |
| 4 | `x = 1232`, `reversedHalf = 1` | Extract last digit (`2`), add to `reversedHalf`, remove from `x` | `x = 123`, `reversedHalf = 12` |
| 4 | `x = 123`, `reversedHalf = 12` | Extract last digit (`3`), add to `reversedHalf`, remove from `x` | `x = 12`, `reversedHalf = 123` |
| 5 | `x = 12`, `reversedHalf = 123` | Exit while loop, check if `x` equals `reversedHalf` or `reversedHalf / 10` | `x` equals `reversedHalf / 10` (`12 == 123 / 10`) |
|  | `x = 12`, `reversedHalf = 123` | Return result | `true` |
## Code
```java
class Solution {
    public boolean isPalindrome(int x) {
        if (x < 0 || (x % 10 == 0 && x != 0)) return false;

        int reversedHalf = 0;

        while (x > reversedHalf) {
            int digit = x % 10;
            reversedHalf = reversedHalf * 10 + digit;
            x = x / 10;
        }
        return (x == reversedHalf) || (x == reversedHalf / 10);
    }
}
```