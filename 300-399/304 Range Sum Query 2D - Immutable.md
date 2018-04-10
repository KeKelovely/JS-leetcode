[Range Sum Query 2D - Immutable](https://leetcode.com/problems/range-sum-query-2d-immutable/description/)

### 问题描述
Given a 2D matrix matrix, find the sum of the elements inside the rectangle defined by its upper left corner (row1, col1) and lower right corner (row2, col2).

Range Sum Query 2D
The above rectangle (with the red border) is defined by (row1, col1) = (2, 1) and (row2, col2) = (4, 3), which contains sum = 8.

Example:
```
Given matrix = [
  [3, 0, 1, 4, 2],
  [5, 6, 3, 2, 1],
  [1, 2, 0, 1, 5],
  [4, 1, 0, 1, 7],
  [1, 0, 3, 0, 5]
]
```
sumRegion(2, 1, 4, 3) -> 8
sumRegion(1, 1, 2, 2) -> 11
sumRegion(1, 2, 2, 4) -> 12
Note:
You may assume that the matrix does not change.
There are many calls to sumRegion function.
You may assume that row1 ≤ row2 and col1 ≤ col2.
### 解法描述
1. 和上一题解法一模一样，只不过多了一层循环而已，注意数组的表示方式，同时用this.matrix指定方法指向的对象
### 源码
```
/**
 * @param {number[][]} matrix
 */
var NumMatrix = function(matrix) {
    this.matrix = matrix;
    for (let i = 0; i < matrix.length; i++){
        for (let j = 1; j < matrix[0].length; j++){
            this.matrix[i][j] += this.matrix[i][j-1];
        }
    }
};

/** 
 * @param {number} row1 
 * @param {number} col1 
 * @param {number} row2 
 * @param {number} col2
 * @return {number}
 */
NumMatrix.prototype.sumRegion = function(row1, col1, row2, col2) {
    let sum = 0;
    for (let k = row1; k <= row2; k++){
        if (col1 === 0){
            sum += this.matrix[k][col2];
        }else {
            sum += this.matrix[k][col2] - this.matrix[k][col1-1];
        }
    }
    return sum;
};

/** 
 * Your NumMatrix object will be instantiated and called as such:
 * var obj = Object.create(NumMatrix).createNew(matrix)
 * var param_1 = obj.sumRegion(row1,col1,row2,col2)
 */
```
