[Pascal's Triangle II](https://leetcode.com/problems/pascals-triangle-ii/description/)
### 问题描述

Given an index k, return the kth row of the Pascal's triangle.

For example, given k = 3,

Return [1,3,3,1].

### 解法
1. 和上题118一模一样的思路，注意这里的起始数字不一样，k=3时实际上对应的是上一题的numRow = 4的情形

### 源码
```
/**
 * @param {number} rowIndex
 * @return {number[]}
 */
var getRow = function(rowIndex) {
            var res = [];
            if (rowIndex === 0){
                return [1];
            }
            for (var i = 0; i < rowIndex+1; i++){
                var tmp = [];
                tmp.length = i+1;
                tmp[0] = 1, tmp[i] = 1;
                for (var j = 1; j < i; j++){
                    tmp[j] = res[i-1][j-1] + res[i-1][j];
                }
            res.push(tmp);
            }
            return res[rowIndex];
};
```
### 运行时间

34 / 34 test cases passed.

Status: Accepted

Runtime: 64 ms

Your runtime beats 64.91 % of javascript submissions.
