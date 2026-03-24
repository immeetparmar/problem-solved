# 61. Rotate List

**LeetCode Problem:** [Rotate List](https://leetcode.com/problems/rotate-list/)

## Approach
The approach to solving the "Rotate List" problem involves first calculating the length of the linked list and then connecting the tail to the head to form a circular linked list. This allows for efficient rotation by finding the new tail and head nodes.

Here's a step-by-step breakdown:
1. **Step 1**: Check if the input linked list is empty, has only one node, or if the rotation count is zero. If any of these conditions are met, return the original list as it is.
2. **Step 2**: Calculate the length of the linked list by traversing it from the head to the tail.
3. **Step 3**: Connect the tail of the linked list to the head to form a circular linked list.
4. **Step 4**: Calculate the actual number of steps to rotate the list by taking the modulus of the rotation count with the length of the list.
5. **Step 5**: Find the new tail node by moving a pointer a certain number of steps from the head.
6. **Step 6**: Find the new head node by moving one step from the new tail node.
7. **Step 7**: Break the circular linked list at the new tail node to get the rotated linked list.

- **Time Complexity**: O(L), where L is the length of the linked list, as we traverse the list to calculate its length and find the new tail and head nodes.
- **Space Complexity**: O(1), as we only use a constant amount of space to store the temporary nodes and variables.

## Dry Run
Let's take the example input: `head = [1, 2, 3, 4, 5]` and `k = 2`.

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `head = [1, 2, 3, 4, 5]`, `k = 2` | Check if the list is empty, has one node, or if `k` is zero | Continue to the next step |
| 2 | `head = [1, 2, 3, 4, 5]` | Calculate the length of the linked list | `length = 5` |
| 3 | `head = [1, 2, 3, 4, 5]`, `length = 5` | Connect the tail to the head to form a circular linked list | `tail.next = head` |
| 4 | `k = 2`, `length = 5` | Calculate the actual number of steps to rotate the list | `k = 2 % 5 = 2`, `steps = 5 - 2 = 3` |
| 5 | `head = [1, 2, 3, 4, 5]`, `steps = 3` | Find the new tail node | `newTail = [3]` |
| 6 | `newTail = [3]` | Find the new head node | `newHead = [4]` |
| 7 | `newTail = [3]`, `newHead = [4]` | Break the circular linked list at the new tail node | `newTail.next = null`, `result = [4, 5, 1, 2, 3]` |

The final output of the algorithm is `[4, 5, 1, 2, 3]`, which is the rotated linked list.
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
    public ListNode rotateRight(ListNode head, int k) {
        if (head == null || head.next == null || k == 0) return head;

        ListNode temp = head;
        int length = 1;

        while (temp.next != null) {
            temp = temp.next;
            length++;
        }
        temp.next = head;

        k = k % length;
        int steps = length - k;

        ListNode newTail = head;
        for (int i = 1; i < steps; i++) {
            newTail = newTail.next;
        }

        ListNode newHead = newTail.next;
        newTail.next = null;

        return newHead;
    }
}
```