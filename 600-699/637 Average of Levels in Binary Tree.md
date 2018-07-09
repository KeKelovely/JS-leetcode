# 问题
[Click me!](https://leetcode.com/problems/average-of-levels-in-binary-tree/description/)
# 解法
1. 本题要求出一颗二叉树中每层节点的平均数，这里用递归的方法来实现
2. 每一层遍历时，首先判断数组是否为空（有没有节点值），没有则push，然后累计求和
3. 最后得到一个res数组与count数组，其中res数组表示每一层节点之和，count数组表示每一层的节点个数，求个平均值即可
4. 求平均值，本质上还是将本题转化为分别求各层的节点之和与节点数，利用递归来实现，需要新定义一个average函数
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
 * @return {number[]}
 */
var averageOfLevels = function(root) {
    var count = []
    var res = []
    average(root, 0, res, count);
    for (var i = 0; i < res.length; i++) {
        res[i] = res[i] / count[i]
    }
    return res
};

var average = function (node, i, sum, count) {
    if (node == null) {
        return
    }
    if (i < sum.length) {
        sum[i] += node.val
        count[i] += 1
    } else {
        sum.push(node.val)
        count.push(1)
    }
    average(node.left, i+1, sum, count)
    average(node.right, i+1, sum, count)
}
```
