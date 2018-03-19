[Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/description/)
### 问题描述
Given a binary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

For example:
Given binary tree [3,9,20,null,null,15,7],
```
    3
   / \
  9  20
    /  \
   15   7
```
return its depth = 3.

### 递归解法
1. 基本操作，注意在递归的基础上每次加1，从而统计树的深度。

### 源码实现
```
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number}
 */
var maxDepth = function(root) {
        if (root === null){
            return 0;
        }else{
            return Math.max(maxDepth(root.left),maxDepth(root.right)) + 1;
        }
};
```
### 运行时间

39 / 39 test cases passed.

Status: Accepted

Runtime: 68 ms

Your runtime beats 93.38 % of javascript submissions.
