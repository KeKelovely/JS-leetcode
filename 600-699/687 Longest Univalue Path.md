# 问题
[CLICK ME](https://leetcode.com/problems/longest-univalue-path/description/)
# 解法
1. 本题要求出最长的相同节点值的路径，使用递归来实现
2. 对左右分别递归，注意要将左右子树的递归结果求和
3. 在递归函数中，若节点值和父节点值不同则返回0，相同则返回1+递归的结果

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
var longestUnivaluePath = function(root) {
    if (!root) return 0
    var tmp = Math.max(longestUnivaluePath(root.left), longestUnivaluePath(root.right))
    return Math.max(tmp, searchLongest(root.left, root.val) + searchLongest(root.right, root.val))
};

var searchLongest = function (node, parentValue) {
    if (!node || node.val != parentValue) return 0
    return 1 + Math.max(searchLongest(node.left, parentValue), searchLongest(node.right, parentValue))
}
```
