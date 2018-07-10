# 问题
[CLICK ME](https://leetcode.com/problems/image-smoother/description/)

# 解法
1. 本题要求出每一个矩阵元素及其四周共计九个元素（包括它）自身在内的平均值，如果边界不存在元素，则只计算那些有的元素
2. 这题就是注意判断一下边界情况即可
- 水平方向上（m），循环的初始值是0（边界）或左边的第一个元素，循环的结束值是rows-1（边界）或右边的第一个元素
- 垂直方向上（n），循环的初始值是0（边界）或上边的第一个元素，循环的结束值是cols-1（边界）或下边的第一个元素

# 代码
```
/**
 * @param {number[][]} M
 * @return {number[][]}
 */
var imageSmoother = function(M) {
    var rows = M.length
    var cols = M[0].length
    var res = []
    for (var i = 0; i < rows; i++) {
        res.push([])
        for (var j = 0; j < cols; j++) {
            var sum = 0
            var count = 0
            for (var m = Math.max(0, i-1); m <= Math.min(rows-1, i+1); m++) {
                for (var n = Math.max(0, j-1); n <= Math.min(cols-1, j+1); n++) {
                    sum += M[m][n]
                    count++
                }
            }
            res[i].push(parseInt(sum / count))
        }
    }
    return res
};
```
