[Symmetric Tree](https://leetcode.com/problems/symmetric-tree/description/)

### 问题描述
Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

For example, this binary tree [1,2,2,3,4,4,3] is symmetric:
```
    1
   / \
  2   2
 / \ / \
3  4 4  3
```
But the following [1,2,2,null,3,null,3] is not:
```
    1
   / \
  2   2
   \   \
   3    3
```
Note:
Bonus points if you could solve it both recursively and iteratively.

### 递归解法
1. 基本操作，首先判断根节点的情况，若根节点不为空，那么直接判断root.left和root.right的情况，用递归实现
2. 注意左右顺序不要搞反了，依次是“左右节点的值是否相等” && “左节点的左儿子和右节点的右儿子” && “左节点的右儿子和右节点的左儿子”
> 最好结合示例中树的图形来理解，照着图写代码

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
var isSymmetric = function(root) {
        if (root === null){
            return true;
        }
        return isST(root.left,root.right);
};
var isST = function(left,right){
        var l = left,
            r = right;
        if (l === null && r === null){
            return true;
        }else if (l !== null && r !== null){
            return (l.val === r.val) && isST(l.left,r.right) && isST(l.right,right.left);
        }else{
            return false;
        }
};
```

### 运行时间

193 / 193 test cases passed.

Status: Accepted

Runtime: 68 ms

Your runtime beats 86.01 % of javascript submissions.

### 迭代解法：待补充
