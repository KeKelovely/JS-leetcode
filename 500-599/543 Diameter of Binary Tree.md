# 问题
[Click me](https://leetcode.com/problems/diameter-of-binary-tree/description/)
# 解法
1. 求一颗二叉树中的最长路径（可能经过or不经过根节点）
2. 当然还是用递归实现啦，用一个max来存储最长路径值，分别计算左子树和右子树的最长路径并相加，注意最后返回左右路径的最大值+1
# 代码
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
var diameterOfBinaryTree = function(root) {
    var max = 0;
    var maxDepth = function(root) {
            if (root === null){
                return 0;
            }else {        
            var left = maxDepth(root.left);
            var right = maxDepth(root.right);
            max = Math.max(max, left + right);
            return Math.max(left, right) + 1;   
        }
    };
    maxDepth(root);
    return max;
};
```
