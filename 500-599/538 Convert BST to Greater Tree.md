# 问题
[Click me](https://leetcode.com/problems/convert-bst-to-greater-tree/description/)
# 解法
1. 本题的意思是给BST树中的每一个节点加上所有比它大的节点的值（大概这个意思，建议看英文描述更加准确）
2. 这里用递归处理即可，考虑到BST的特点，首先求根节点右子树的所有convert结果（因为右节点一定比左节点大），然后再求左子树结果，最后从根节点遍历。
3. 本题求和比较简单，重点是考虑到BST的特点，采用先右后左的方式递归，不要弄反顺序。
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
 * @return {TreeNode}
 */
var convertBST = function(root) {
    var sum = 0;
    var convert = function(node) {
        if (node === null ) {
            return;
        }    
        convert(node.right);
        sum += node.val;
        node.val = sum;
        convert(node.left);
    }
        convert(root);
        return root;
    };


```
