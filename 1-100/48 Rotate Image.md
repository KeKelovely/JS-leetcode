[Rotate Image](https://leetcode.com/problems/rotate-image/description/)
### 问题描述
You are given an n x n 2D matrix representing an image.

Rotate the image by 90 degrees (clockwise).

Note:
You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation.

Example 1:
```
Given input matrix = 
[
  [1,2,3],
  [4,5,6],
  [7,8,9]
],

rotate the input matrix in-place such that it becomes:
[
  [7,4,1],
  [8,5,2],
  [9,6,3]
]
```
Example 2:
```
Given input matrix =
[
  [ 5, 1, 9,11],
  [ 2, 4, 8,10],
  [13, 3, 6, 7],
  [15,14,12,16]
], 

rotate the input matrix in-place such that it becomes:
[
  [15,13, 2, 5],
  [14, 3, 4, 1],
  [12, 6, 8, 9],
  [16, 7,10,11]
]
```
### 问题解法：
1. 矩阵旋转问题
2. 原来的思路是寻找新旧矩阵元素间的映射关系，但注意，在变换时，映射操作必须借助一个中间（空）矩阵来实现，无法满足题目要求的“you have to modify the input 2D matrix directly”
3. 当映射解法失效时，能够做的就是对矩阵元素进行交换，即通过**交换矩阵元素**的方法实现
4. 解法：原矩阵 → 沿对角线翻转 → 上下翻转 → 目标矩阵
5. 理解了交换元素的方法，再找元素的对应关系即可。剩下都是基本操作。

### 源码实现
```
/**
 * @param {number[][]} matrix
 * @return {void} Do not return anything, modify matrix in-place instead.
 */
var rotate = function(matrix) {
        var m = matrix[0].length,
            n = matrix.length;
        for (var i = 0; i < m-1; i++){
            for (var j = 0; j < n-1-i; j++){
            [matrix[i][j], matrix[n - 1 - j][n - 1 - i]] = [matrix[n - 1 - j][n - 1 - i],matrix[i][j]];
            }
        }
        for (var i = 0; i < n/2; i++){
            for (var j = 0; j < m; j++){
            [matrix[i][j], matrix[n - 1 - i][j]] = [matrix[n - 1 - i][j],matrix[i][j]];
            }
        }
};
```

### 时间

21 / 21 test cases passed.

Status: Accepted

Runtime: 68 ms

Your runtime beats 52.32 % of javascript submissions.

~~最快的那位老哥似乎只用了45ms..有待优化~~

### 优化一
1. 更改旋转矩阵的方式，先求原始矩阵的→ 转置矩阵（即沿着对角线翻转），再沿着中心对称轴翻转（直接将每个数组元素reverse），所得即为目标矩阵
2. 这样可以将原有的两次双重循环减少为一次。
3. 目测应该可以用多个单循环来写，就是代码会麻烦点
```
/**
 * @param {number[][]} matrix
 * @return {void} Do not return anything, modify matrix in-place instead.
 */
var rotate = function(matrix) {
        var m = matrix[0].length, // m表示矩阵的列，即横向长
            n = matrix.length; // n表示矩阵的行，即纵向长
        for (var i = 0; i < m; i++){
            for (var j = i+1; j < m; j++){
                [ matrix[i][j], matrix[j][i] ] = [ matrix[j][i],matrix[i][j]  ];
            }
                matrix[i].reverse();
        }
};
```
### 运行时间

21 / 21 test cases passed.

Status: Accepted

Runtime: 60 ms

Your runtime beats 79.75 % of javascript submissions.
