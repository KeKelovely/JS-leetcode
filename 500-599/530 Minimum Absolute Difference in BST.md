# 问题
[Click me](https://leetcode.com/problems/minimum-absolute-difference-in-bst/description/)
# 解法
1. 本题要求求出**在BST中任意两个树节点间的最短距离**，考虑到BST的特点，对BST进行中序遍历得到一个有序数组，然后只需要比较相邻元素间的差值，找出min值即可。
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
var getMinimumDifference = function(root) {
    var arr = [],
        res = Number.MAX_VALUE;
    inOrder(arr, root);
    for (var i = 1; i < arr.length; i++) {
        res = Math.min(res, arr[i] - arr[i-1]);
    }
    return res;
};

var inOrder = function(arr, root) {
    if (!root) return;
    inOrder(arr, root.left);
    arr.push(root.val);
    inOrder(arr, root.right);
};
```
