# 问题
[CLICK ME](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/description/)
# 解法
1. 本题是Two Sum的二叉树情形，即给一个数k，问在一颗二叉树中是否可以找到两个节点值a,b 使得a+b = k?
2. 同样此处用递归的方法处理，每次递归将一个节点中的值放入一个临时数组arr中，然后使用indexOf方法查找是否存在满足要求的数
3. 最后根据不同的情况返回true或false，然后依次对左右子树递归

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
 * @param {number} k
 * @return {boolean}
 */
var findTarget = function(root, k) {
    if (!root) {
        return false
    }
    var arr = []
    return findSum(root, k, arr)
};

var findSum = function(node, k, arr) {
    if (!node) {
        return false
    }
    if (arr.indexOf(k - node.val) != -1) {
        return true
    }
    arr.push(node.val)
    return findSum(node.left, k, arr) || findSum(node.right, k, arr)
}
```
