# 876. Middle of the Linked List

**LeetCode Problem:** [Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)

## Approach
The approach used to solve the "Middle of the Linked List" problem is the two-pointer technique, where two pointers, `slow` and `fast`, traverse the linked list at different speeds. This technique allows us to find the middle node of the linked list in a single pass.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Initialize two pointers, `slow` and `fast`, to the head of the linked list.
2. **Step 2**: Traverse the linked list using a while loop, where `fast` moves two steps at a time and `slow` moves one step at a time.
3. **Step 3**: The loop continues until `fast` reaches the end of the linked list or `fast.next` becomes null.
4. **Step 4**: When the loop ends, `slow` will be pointing to the middle node of the linked list.

- **Time Complexity**: The time complexity of this solution is O(n), where n is the number of nodes in the linked list, because we are traversing the linked list only once.
- **Space Complexity**: The space complexity of this solution is O(1), because we are using a constant amount of space to store the two pointers.

## Dry Run

Let's consider an example input: a linked list with the nodes 1 -> 2 -> 3 -> 4 -> 5.

Here's the execution of the algorithm in a step-by-step table format:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | slow = head (1), fast = head (1) | Initialize slow and fast pointers | slow = 1, fast = 1 |
| 2 | slow = 1, fast = 1 | fast moves two steps, slow moves one step | slow = 2, fast = 3 |
| 3 | slow = 2, fast = 3 | fast moves two steps, slow moves one step | slow = 3, fast = 5 |
| 4 | slow = 3, fast = 5 | fast moves two steps, but since fast.next is null, the loop ends | slow = 3 |
| 5 | slow = 3 | Return the slow pointer, which points to the middle node | Output: 3 |

In this example, the middle node of the linked list is the node with value 3, which is correctly returned by the algorithm.
## Code
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode middleNode(ListNode head) {
        ListNode slow = head, fast = head;

        while(fast != null && fast.next != null){
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
    }
}
```