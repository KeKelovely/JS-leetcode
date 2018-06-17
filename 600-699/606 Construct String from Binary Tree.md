# 问题
[Click me](https://leetcode.com/problems/construct-string-from-binary-tree/description/)
# 解法
1. 本题需要将一颗二叉树转换为带括号的字符串。当然还是用递归来做，每次递归返回一个字符串（结点值转换为String的结果）
2. 然后分情况讨论，如题意所示，如果右子树存在，这时才会给左右添加上括号，若不存在，则不会加括号。
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
 * @param {TreeNode} t
 * @return {string}
 */
var tree2str = function(t) {
    if (t == null) return ""
    var res = String(t.val)
    if (t.left == null && t.right == null) return res
    res += "(" + tree2str(t.left) + ")"
    if (t.right != null) res+= "(" + tree2str(t.right) + ")"
    return res
};
```
