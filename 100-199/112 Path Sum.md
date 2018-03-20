[Path Sum](https://leetcode.com/problems/path-sum/description/)
### 问题描述
Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

For example:
Given the below binary tree and sum = 22,
```
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \      \
        7    2      1
 ```
return true, as there exist a root-to-leaf path 5->4->11->2 which sum is 22.


### 解法：递归实现
1. 给定一个sum值，找到一棵树上的路径，使得这条路径上所有节点的值的和等于sum值。
2. 注意这里要求的是"a root-to-leaf path"，所以递归需要递归到叶节点为止，换言之，要求root.left === null && root.right === null
3. 最后依次对左右子树递归遍历即可。

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
 * @param {number} sum
 * @return {boolean}
 */
var hasPathSum = function(root, sum) {
        if (root === null){
            return false;
        }
        if ((root.val === sum) && (root.left === null) && (root.right === null)){
            return true;
        }
        return hasPathSum(root.left,sum-root.val) || hasPathSum(root.right,sum-root.val);
};
```
### 运行时间

114 / 114 test cases passed.

Status: Accepted

Runtime: 80 ms

Your runtime beats 54.51 % of javascript submissions.
