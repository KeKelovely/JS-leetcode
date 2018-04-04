[Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/description/)
### 问题描述
Invert a binary tree.
```
     4
   /   \
  2     7
 / \   / \
1   3 6   9
```
to
```
     4
   /   \
  7     2
 / \   / \
9   6 3   1
```

### 解法描述
1. 转换一颗二叉树，显然使用递归方法就好啦
2. 交换root.left与root.right时注意使用一个中间变量tmp来保存其中一颗子树的节点，防止丢失

### 源码实现
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
 * @return {TreeNode}
 */
var invertTree = function(root) {
	if (!root){
		return null;
	}
	var tmp = root.left;
	root.left = invertTree(root.right);
	root.right = invertTree(tmp);
	return root;
};
```
