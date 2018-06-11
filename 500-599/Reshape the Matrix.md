# 问题描述

[Click me](https://leetcode.com/problems/reshape-the-matrix/description/)

# 解法

### 总结
凡是涉及到矩阵变换的问题，首先考虑新旧矩阵间的**坐标关系**，找出变换前后坐标关系，答案就显而易见了。

1. 对本题，首先做一个判断，如果r*c的元素个数与原矩阵的元素个数不相等，则依照题意直接返回原矩阵。
2. 若相等，则对所有的元素个数进行遍历，在遍历过程中，展开坐标变换，其中行坐标由i/c表示（注意取整），（可以这么想，矩阵有多少行？显然就是总数除列数），列坐标表示一列有几个数？当然用i%c来表示
3. 找到对应关系后，进行赋值即可

# Code

```
/**
 * @param {number[][]} nums
 * @param {number} r
 * @param {number} c
 * @return {number[][]}
 */
var matrixReshape = function(nums, r, c) {
    var row = nums.length,
        col = nums[0].length,
        tmp = [],
        res = [];
    for (var i = 0; i < r; i++) {
        res.push([]);
    }
    if ( r * c == row * col) {
        for (var j = 0; j < r * c; j++) {
            res[parseInt(j / c)][j % c] = nums[parseInt(j / col)][j % col];
        }
        return res;
    }else {
        return nums;
    }
};
```
