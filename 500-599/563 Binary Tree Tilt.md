# 问题
[Click me](https://leetcode.com/problems/binary-tree-tilt/description/)
# 解法
1. 本题要求二叉树的倾斜度（每个节点左右子树节点之和的差值，最后累加起来就是倾斜度tilt）
2. 本题比较简单，分别对左右子树递归求和，然后在求和过程中求左右差值，并累加到res中，最后返回res即可
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



var findTilt = function(root) {
    var res = 0;
    var sumNode = function(node) {
        if (node === null) {
            return 0;
        } 
        var left_sum = sumNode(node.left);
        var right_sum = sumNode(node.right);

        res += Math.abs(left_sum - right_sum);

        return left_sum + right_sum + node.val;
    };
    
    var tmp = sumNode(root);
    return res;
};
```
