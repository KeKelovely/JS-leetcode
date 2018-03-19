[Binary Tree Level Order Traversal II](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/description/)
### 问题描述
Given a binary tree, return the bottom-up level order traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).

For example:
Given binary tree [3,9,20,null,null,15,7],
```
    3
   / \
  9  20
    /  \
   15   7
 ```
return its bottom-up level order traversal as:
[
  [15,7],
  [9,20],
  [3]
]

### 目前能想到的解法
1. 顺序操作，从上往下依次遍历整棵树，用变量level表示每一层的层数，按照push方法依次将元素从尾部插入
2. 这样最后得到的就是一个top-bottom的顺序，然后将所得结果的Array用reverse()方法，即可得到bottom-top顺序
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
 * @return {number[][]}
 */
var levelOrderBottom = function(root) {
        var res = [];
        levelorder(root,0,res);
        return res.reverse();
};
var levelorder = function(root,level,res){
        if (!root){
            return; 
        }
        if (res.length === level){
            res.push([]);
        }
        res[level].push(root.val);
        if (root.left){
            levelorder(root.left,level+1,res);
        }
        if (root.right){
            levelorder(root.right,level+1,res);
        }
};
```
### 运行时间

34 / 34 test cases passed.

Status: Accepted

Runtime: 64 ms

Your runtime beats 74.42 % of javascript submissions.
