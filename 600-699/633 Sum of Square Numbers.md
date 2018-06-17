# 问题
[Click Me](https://leetcode.com/problems/sum-of-square-numbers/description/)
# 解法
1. 本题要求判断一个数是否可以被分为两个数的平方和，由题意知a^2 <= c, 那么a <= sqrt(c)，因此只需遍历到sqrt(c)即可
2. 接下来就不用再套一层循环（否则会超时），注意到此时c已知，a已知（就是循环变量i），那么b是可以求出来的
3. 最后只需要判断b开根号后的结果是否为整数（用parseInt），若结果为整数，说明存在符合要求的b，返回true
# 代码
```
/**
 * @param {number} c
 * @return {boolean}
 */
var judgeSquareSum = function(c) {
  for (var i = 0; i <= Math.sqrt(c); i++) {
      var squreB = c - i * i
      if (Math.sqrt(squreB) == parseInt(Math.sqrt(squreB))) return true
  }
  return false
};
```
