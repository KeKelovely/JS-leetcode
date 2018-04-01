[Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/description/)
### 问题描述
Write a function that takes an unsigned integer and returns the number of ’1' bits it has (also known as the Hamming weight).

For example, the 32-bit integer ’11' has binary representation 00000000000000000000000000001011, so the function should return 3.

### 解法描述
1. 和上一题类似，利用n & 1操作每次取32位数的尾数（1或者0）
2. 然后将n右移1位，去掉已经统计过的尾数，形成类似递归的效果

### 源码
```
/**
 * @param {number} n - a positive integer
 * @return {number}
 */
var hammingWeight = function(n) {
    var res = 0;
    for (var i = 0; i < 32; i++){
        res += (n & 1);
        n >>= 1;
    }
    return res;
};
```
### 运行时间

600 / 600 test cases passed.

Status: Accepted

Runtime: 64 ms

Your runtime beats 96.88 % of javascript submissions.
