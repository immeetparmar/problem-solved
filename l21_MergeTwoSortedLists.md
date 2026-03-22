# 21. Merge Two Sorted Lists

**LeetCode Problem:** [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

## Approach
The approach to solving the "Merge Two Sorted Lists" problem involves creating a dummy node to simplify the merging process and then iteratively comparing nodes from the two input lists to construct the merged list. This process continues until all nodes from both lists have been incorporated into the merged list.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Initialize a dummy node (`dummy`) and a current pointer (`current`) to keep track of the last node in the merged list.
2. **Step 2**: Enter a loop that continues as long as there are nodes in both `list1` and `list2`. Inside the loop, compare the values of the current nodes in `list1` and `list2`.
3. **Step 3**: Based on the comparison, append the node with the smaller value to the merged list by updating `current.next` and then move the corresponding list pointer (`list1` or `list2`) to the next node.
4. **Step 4**: After the loop, if there are remaining nodes in either `list1` or `list2`, append them to the end of the merged list.
5. **Step 5**: Finally, return the next node of the dummy node (`dummy.next`) as the head of the merged list.

- **Time Complexity**: The time complexity is O(n + m), where n and m are the lengths of `list1` and `list2`, respectively, because each node is visited once.
- **Space Complexity**: The space complexity is O(n + m) for the merged list, but if we exclude the space needed for the output, the extra space used is O(1) for the dummy node and other variables.

## Dry Run
Let's consider an example where `list1` is 1 -> 3 -> 5 and `list2` is 2 -> 4 -> 6. The dry run of the algorithm would look like this:

| Step Number | Current State of Variables | Action Taken | Result/Output |
| --- | --- | --- | --- |
| 1 | `dummy` = new ListNode(0), `current` = `dummy`, `list1` = 1 -> 3 -> 5, `list2` = 2 -> 4 -> 6 | Initialize dummy node and current pointer | `dummy` = 0, `current` = 0 |
| 2 | `list1` = 1 -> 3 -> 5, `list2` = 2 -> 4 -> 6 | Compare `list1.val` (1) and `list2.val` (2), append smaller node to merged list | `current.next` = 1, `list1` = 3 -> 5, `current` = 1 |
| 3 | `list1` = 3 -> 5, `list2` = 2 -> 4 -> 6 | Compare `list1.val` (3) and `list2.val` (2), append smaller node to merged list | `current.next` = 2, `list2` = 4 -> 6, `current` = 2 |
| 4 | `list1` = 3 -> 5, `list2` = 4 -> 6 | Compare `list1.val` (3) and `list2.val` (4), append smaller node to merged list | `current.next` = 3, `list1` = 5, `current` = 3 |
| 5 | `list1` = 5, `list2` = 4 -> 6 | Compare `list1.val` (5) and `list2.val` (4), append smaller node to merged list | `current.next` = 4, `list2` = 6, `current` = 4 |
| 6 | `list1` = 5, `list2` = 6 | Compare `list1.val` (5) and `list2.val` (6), append smaller node to merged list | `current.next` = 5, `list1` = null, `current` = 5 |
| 7 | `list1` = null, `list2` = 6 | Append remaining node from `list2` to merged list | `current.next` = 6, `list2` = null |
| 8 | - | Return `dummy.next` as the head of the merged list | Merged list = 1 -> 2 -> 3 -> 4 -> 5 -> 6 |
## Code
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 * int val;
 * ListNode next;
 * ListNode() {}
 * ListNode(int val) { this.val = val; }
 * ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {

        ListNode dummy = new ListNode(0);
        ListNode current = dummy;

        while (list1 != null && list2 != null) {
            if (list1.val <= list2.val) {
                current.next = list1;
                list1 = list1.next;
            } else {
                current.next = list2;
                list2 = list2.next;
            }
            current = current.next;
        }

        if (list1 != null) {
            current.next = list1;
        } else {
            current.next = list2;
        }
        return dummy.next;
    }
}
```