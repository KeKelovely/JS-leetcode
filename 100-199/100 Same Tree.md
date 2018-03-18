[Same Tree](https://leetcode.com/problems/same-tree/description/)

### 问题描述
Given two binary trees, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical and the nodes have the same value.


Example 1:
```
Input:     1         1
          / \       / \
         2   3     2   3

        [1,2,3],   [1,2,3]

Output: true
```

Example 2:
```
Input:     1         1
          /           \
         2             2

        [1,2],     [1,null,2]

Output: false
```

Example 3:
```
Input:     1         1
          / \       / \
         2   1     1   2

        [1,2,1],   [1,1,2]

Output: false
```
### 解法：递归方法
1. 递归递归递归...重要的事情说三遍
2. 分情况讨论
- p,q节点均不存在，返回true
- p,q节点只存在其中一个，另一个为null，返回false
- p,q节点都存在，比较p.val与q.val，然后对左右子树分别递归

### 代码实现
```
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} p
 * @param {TreeNode} q
 * @return {boolean}
 */
var isSameTree = function(p, q) {
        if (!p && !q){
            return true;
        }
        if ((p && !q) || (!p && q) || (p.val !== q.val)){
            return false;
        }
        return isSameTree(p.left,q.left) && isSameTree(p.right,q.right);
};
```
### 运行时间

57 / 57 test cases passed.

Status: Accepted

Runtime: 60 ms

Your runtime beats 75.00 % of javascript submissions.
