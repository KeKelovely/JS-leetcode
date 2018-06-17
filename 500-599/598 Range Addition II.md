# 问题
[click me](https://leetcode.com/problems/range-addition-ii/description/)
# 解法
1. 找出数组经过变换后的最大值的元素个数，感觉这里比较简单，因为只是求个数，每次循环找最小值即可
2. 循环完后还要与矩阵自身的m、n进行比较，最后取最小的值并返回结果的乘积
# 代码
```
/**
 * @param {number} m
 * @param {number} n
 * @param {number[][]} ops
 * @return {number}
 */
var maxCount = function(m, n, ops) {
  var mr = Number.MAX_VALUE
  var mc = Number.MAX_VALUE
  for (var i = 0; i < ops.length; i++) {
      mr = Math.min(mr, ops[i][0])
      mc = Math.min(mc, ops[i][1])
  }
  mr = Math.min(mr, m)
  mc = Math.min(mc, n)
  return mr * mc
};
```
