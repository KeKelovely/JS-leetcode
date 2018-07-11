# 问题
[CLICK ME](https://leetcode.com/problems/trim-a-binary-search-tree/description/)
# 解法
1. 本题要求对一颗二叉树进行【修整】，即保留树中所有节点值在[L, R]之间的值，去掉所有不在这一范围的值

2. 同样用递归方法来实现，首先考虑空节点的情形，然后当节点值【不满足条件】的时候，直接向下递归，不作任何操作

3. 具体递归的时候，直接让左右节点等于递归的值即可，因为题目知识要求保留即可。

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
 * @param {number} L
 * @param {number} R
 * @return {TreeNode}
 */
var trimBST = function(root, L, R) {
    if (root == null) {
        return null
    }
    if (root.val < L) return trimBST(root.right, L, R)
    if (root.val > R) return trimBST(root.left, L, R)
    
    root.left = trimBST(root.left, L, R)
    root.right = trimBST(root.right, L, R)
    return root
};
```
