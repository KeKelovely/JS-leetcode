[Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/description/)

### 问题描述
Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

### 解法：递归实现
1. 找一棵树的最小高度，嘛，之前用递归解法求过最大高度，这里是一样的道理。
2. 不过这里不一样的地方是需要加上一个限制条件，若某一（非叶子）节点的左or右节点为null，那么应当去求另一边非空节点的高度，不然这个递归会在非叶子节点处就终止掉。
### 源码
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
var minDepth = function(root) {
        if (root === null){
            return 0;
        }
        if (root.left === null){
            return minDepth(root.right)+1;
        }
        if (root.right === null){
            return minDepth(root.left)+1;
        }
        return Math.min(minDepth(root.left),minDepth(root.right))+1;
};
```
### 运行时间

41 / 41 test cases passed.

Status: Accepted

Runtime: 68 ms

Your runtime beats 92.49 % of javascript submissions.
