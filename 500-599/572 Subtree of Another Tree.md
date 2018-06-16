# 问题
[Click me](https://leetcode.com/problems/subtree-of-another-tree/description/)
# 解法
1. 本题需要判断一棵树是否为另外一颗树的子树，可以将问题转换为一棵树是否**等于另外一颗树的一部分**，因此首先我们写一个函数isSame来判断两棵树是否相等，
然后分别对左右子树遍历即可得到答案。
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
 * @param {TreeNode} s
 * @param {TreeNode} t
 * @return {boolean}
 */
var isSubtree = function(s, t) {
    if (s === null) return false;
    if (isSame(s, t)) return true;
    return isSubtree(s.left, t) || isSubtree(s.right, t);
};

var isSame = function(s, t) {
    if (s === null && t === null) return true;
    if (s === null || t === null) return false;
    if (s.val !== t.val) return false;
    return isSame(s.left, t.left) && isSame(s.right, t.right);
}
```
