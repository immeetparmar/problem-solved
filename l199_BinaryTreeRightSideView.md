# 199. Binary Tree Right Side View

**LeetCode Problem:** [Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/)

## Approach
The approach to solving the "Binary Tree Right Side View" problem involves using a breadth-first search (BFS) algorithm to traverse the tree level by level, adding the last node's value at each level to the result list. This is achieved by utilizing a queue data structure to keep track of nodes at each level.

Here's a step-by-step breakdown of the logic:
1. **Step 1**: Check if the root of the tree is null. If it is, return an empty list as there are no nodes to process.
2. **Step 2**: Initialize a queue with the root node and a list to store the result.
3. **Step 3**: Enter a loop that continues until the queue is empty, indicating that all levels of the tree have been processed.
4. **Step 4**: Within the loop, determine the number of nodes at the current level by getting the size of the queue.
5. **Step 5**: Process each node at the current level by removing it from the queue, checking if it's the last node at the level, and adding its value to the result list if it is.
6. **Step 6**: Add the left and right children of the current node to the queue if they exist, preparing for the next level's processing.
7. **Step 7**: Repeat steps 4 through 6 until the queue is empty, at which point all levels have been processed and the result list contains the right side view of the tree.

- **Time Complexity**: The time complexity of this algorithm is O(N), where N is the number of nodes in the tree, since each node is visited once.
- **Space Complexity**: The space complexity is O(N) as well, due to the space required for the queue in the worst case (when the tree is a complete binary tree and the last level is fully occupied).

## Dry Run

Let's consider a sample binary tree with the following structure:
```
    1
   / \
  2   3
 / \   \
4   5   6
```
Here's how the algorithm would execute on this tree:

| Step number | Current state of variables | Action taken | Result/Output |
| --- | --- | --- | --- |
| 1 | root = 1, mylist = [] | Check if root is null | root is not null, proceed |
| 2 | queue = [1], mylist = [] | Add root to queue | queue = [1] |
| 3 | queue = [1], mylist = [] | Start loop, size = 1 | |
| 4 | queue = [1], mylist = [] | Remove node 1 from queue, check if last node at level | mylist = [1] |
| 5 | queue = [], mylist = [1] | Add children of node 1 to queue | queue = [2, 3] |
| 6 | queue = [2, 3], mylist = [1] | Repeat loop, size = 2 | |
| 7 | queue = [2, 3], mylist = [1] | Remove node 2 from queue, not last node at level | queue = [3] |
| 8 | queue = [3], mylist = [1] | Remove node 3 from queue, last node at level | mylist = [1, 3] |
| 9 | queue = [], mylist = [1, 3] | Add children of node 3 to queue | queue = [5, 6] |
| 10 | queue = [5, 6], mylist = [1, 3] | Repeat loop, size = 2 | |
| 11 | queue = [5, 6], mylist = [1, 3] | Remove node 5 from queue, not last node at level | queue = [6] |
| 12 | queue = [6], mylist = [1, 3] | Remove node 6 from queue, last node at level | mylist = [1, 3, 6] |
| 13 | queue = [], mylist = [1, 3, 6] | Queue is empty, exit loop | Final result: mylist = [1, 3, 6] |

The final output of the algorithm for this sample tree is `[1, 3, 6]`, which represents the right side view of the tree.
## Code
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public List<Integer> rightSideView(TreeNode root) {
        List<Integer> mylist = new ArrayList<Integer>();
        
        if(root == null){
            return mylist;
        }
        Queue<TreeNode> Que = new LinkedList<>();
        Que.offer(root);
        while(!Que.isEmpty()){
            int size = Que.size();
            for(int i = 1;i<=size;i++){
                TreeNode Nikla = Que.poll();
            
            if(i == size){
                mylist.add(Nikla.val);
            }
            if(Nikla.left!= null){
                Que.offer(Nikla.left);
            }
            if(Nikla.right!= null){
                Que.offer(Nikla.right);
            }
          }
        }
        return mylist;
    }
}
```