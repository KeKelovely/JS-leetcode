[Factorial Trailing Zeroes](https://leetcode.com/problems/factorial-trailing-zeroes/description/)

### 问题描述
Given an integer n, return the number of trailing zeroes in n!.

Note: Your solution should be in logarithmic time complexity.

### 解法描述
1. 给一个整数n，求n！（n的阶乘）的后缀中0的个数
2. 个人以为是一道烂题，基本不涉及任何的算法知识，纯粹是一个数学trick...
3. 只用判断有多少个因子5就行了，注意5中套5的情况..反正就是个奥数题..

### 源码
```
/**
 * @param {number} n
 * @return {number}
 */
var trailingZeroes = function(n) {
            var count = 0;
            while (n){
                count += parseInt(n/5);
                n = parseInt(n/5);
            }
            return count;
};
```
### 运行时间

502 / 502 test cases passed.

Status: Accepted

Runtime: 68 ms

Your runtime beats 80.00 % of javascript submissions.
