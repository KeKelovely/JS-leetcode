# 问题
[Click me](https://leetcode.com/problems/merge-two-binary-trees/description/)
# 解法
1. 本题需要将两颗二叉树合并，首先判断节点为空的情形，若其中一棵树上节点为空，则直接返回另一节点
2. 然后使用构造函数new TreeNode()新建一个节点，存储两个节点的值的和，然后分别对两棵树的左右子树做递归
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
 * @param {TreeNode} t1
 * @param {TreeNode} t2
 * @return {TreeNode}
 */
var mergeTrees = function(t1, t2) {
    if (t1 === null) return t2
    if (t2 === null) return t1
    var t = new TreeNode(t1.val + t2.val)
    t.left = mergeTrees(t1.left, t2.left)
    t.right = mergeTrees(t1.right, t2.right)
    return t
};
```
