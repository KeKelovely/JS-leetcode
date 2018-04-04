[Binary Tree Paths](https://leetcode.com/problems/binary-tree-paths/description/)

### 问题描述
Given a binary tree, return all root-to-leaf paths.

For example, given the following binary tree:
```
   1
 /   \
2     3
 \
  5
```
All root-to-leaf paths are:

["1->2->5", "1->3"]

### 解法描述
1. 找出Root-to-Leaf的路径，这里还是使用递归解法，注意最后的输出形式有点奇葩，需要用到字符串的连接操作，然后逐个递归遍历节点

### 源码
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
 * @return {string[]}
 */
var binaryTreePaths = function(root) {
    var result = [];
    if (root !== null){
    	searchTreePaths(root,"",result);
    }
    return result;
};
var searchTreePaths = function(root,path,res){
	if (root.left === null && root.right === null) res.push(path + root.val);
	if (root.left !== null) searchTreePaths(root.left,path + root.val + '->', res);
	if (root.right !== null) searchTreePaths(root.right,path + root.val + '->', res);
}
```
