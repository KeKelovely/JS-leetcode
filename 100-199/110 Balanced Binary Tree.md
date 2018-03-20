[Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree/description/)
### 问题描述
Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as:

a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

Example 1:

Given the following tree [3,9,20,null,null,15,7]:
```
    3
   / \
  9  20
    /  \
   15   7
```
Return true.

Example 2:

Given the following tree [1,2,2,3,3,null,null,4,4]:
```
       1
      / \
     2   2
    / \
   3   3
  / \
 4   4
 ```
Return false.

### 解法：递归实现
1. 判断一棵树是否为平衡二叉树（详情定义见题干**never differ by more than 1**），本质上可以归结为求左右子树的高度，同样用递归实现
2. 基本思路是分别求左右子树的高度，然后Math.abs(left - right) > 1若成立，说明这不是一颗平衡二叉树，返回false。然后分别root.left以及root.right递归
3. 然后编写一个函数height()用来求某一节点的高度即可。
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
 * @return {boolean}
 */
var isBalanced = function(root) {
        if (root === null){
            return true;
        }
        var left = height(root.left),
            right = height(root.right);
        if (Math.abs(left - right) > 1){
            return false;
        }
        return isBalanced(root.left) && isBalanced(root.right);
};
var height = function(node){
        if (node === null){
            return 0;
        }  else if (node.left === null && node.right === null){
            return 1;
        }else{
            var left = height(node.left),
                right = height(node.right);
            return 1 + (left > right ? left : right);
        }
};
```
### 运行时间

227 / 227 test cases passed.

Status: Accepted

Runtime: 72 ms

Your runtime beats 93.85 % of javascript submissions.

