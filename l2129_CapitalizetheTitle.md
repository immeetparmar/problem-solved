# 2129. Capitalize the Title

**LeetCode Problem:** [Capitalize the Title](https://leetcode.com/problems/capitalize-the-title/)

## Approach
The approach to solving the "Capitalize the Title" problem involves using Java's Stream API to process each word in the input string. It checks the length of each word and capitalizes the first letter if the word has more than two characters.

Here's a step-by-step breakdown:
1. **Step 1**: The input string `title` is converted to lowercase using the `toLowerCase()` method to ensure the rest of the operations are case-insensitive.
2. **Step 2**: The string is split into an array of words using the `split(" ")` method, which divides the string at each space character.
3. **Step 3**: The `Arrays.stream()` method is used to create a stream from the array of words, allowing for the application of various stream operations.
4. **Step 4**: The `map()` function is applied to the stream, transforming each word by checking its length. If the word has more than two characters, it capitalizes the first letter using `Character.toUpperCase()` and leaves the rest of the word unchanged.
5. **Step 5**: Finally, the `collect()` method is used with `Collectors.joining(" ")` to combine the transformed words back into a single string, with each word separated by a space.

- **Time Complexity**: The time complexity of this solution is O(n*m), where n is the number of words in the title and m is the average length of a word. This is because for each word, we potentially iterate over its characters to capitalize it.
- **Space Complexity**: The space complexity is O(n*m) as well, because we create new strings for each word (whether modified or not) and store them in memory before joining them back together.

## Dry Run

Let's consider the input string "hello world a". Here's how the algorithm would process it:

| Step Number | Current State of Variables | Action Taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `title` = "hello world a" | Convert `title` to lowercase | `title` = "hello world a" (no change) |
| 2 | `title` = "hello world a" | Split `title` into words | `words` = ["hello", "world", "a"] |
| 3 | `words` = ["hello", "world", "a"] | Create a stream from `words` | Stream of words: ["hello", "world", "a"] |
| 4 | Stream of words: ["hello", "world", "a"] | Map each word to capitalize if length > 2 | Stream of words: ["Hello", "World", "a"] |
| 5 | Stream of words: ["Hello", "World", "a"] | Collect and join words back into a string | "Hello World a" |

The final output for the input "hello world a" is "Hello World a".
## Code
```java
class Solution {
    public String capitalizeTitle(String title) {
        return Arrays.stream(title.toLowerCase().split(" "))
                .map(word -> word.length() > 2 ? Character.toUpperCase(word.charAt(0)) + word.substring(1) : word)
                .collect(Collectors.joining(" "));
    }
}

```