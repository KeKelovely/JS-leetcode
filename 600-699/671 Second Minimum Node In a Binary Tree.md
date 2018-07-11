# 问题
[CLICK ME](https://leetcode.com/problems/second-minimum-node-in-a-binary-tree/description/)
# 解法
1. 本题要求出一颗特殊二叉树中第二小的节点值，注意本题给定的各种条件，首先，每个节点有0或2个节点，且每个节点值不大于其子节点的值

2. 根据条件，对任意的node.val，必有node.val <= node.left.val && node.val <= node.right.val，那么，根节点必定为最小值

3. 接下来，只需要找出比根节点大一次（或者可以理解为大一层）的节点值就可以了，这里就必须将【等于】和【小于】分情况来讨论

4. 如果等于，那么继续向下递归（因为这时显然不是我们要找的第二小），如果小于，将该节点值存储起来（因为还需要将左右子节点进行比较）

5. 当然，如果该节点的子节点为0，说明不存在第二小，直接返回-1

6. 最后进行判断，如果左右中出现了-1，说明其中至少有一个是子节点为0的节点，换言之，这个子节点为0的节点，必定与上一层节点值相等，它就不是我们要找的，我们要求的是稍大一层的那个数，所以我们比较求最大值即可

7. 如果没有出现-1，说明两个子节点都大于上一级父节点，我们比较找出它们之间的小者，就是我们所求的【第二小】

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
var findSecondMinimumValue = function(root) {
    if (!root.left) return -1
    var left = (root.val == root.left.val) ? findSecondMinimumValue(root.left) : root.left.val
    var right = (root.val == root.right.val) ? findSecondMinimumValue(root.right) : root.right.val
    return (left == -1 || right == -1) ? Math.max(left, right) : Math.min(left, right)
};
```
