# 问题描述
The Hamming distance between two integers is the number of positions at which the corresponding bits are different.

Given two integers x and y, calculate the Hamming distance.

Note:
0 ≤ x, y < 231.

Example:
```
Input: x = 1, y = 4

Output: 2

Explanation:
1   (0 0 0 1)
4   (0 1 0 0)
       ↑   ↑
```
The above arrows point to positions where the corresponding bits are different.

# 解法
1. Hamming distance是指两个数字的二进制对应位上不同数字的个数，既然涉及到了二进制的不同位的比较，当然是使用异或方法。
2. 复习： 异或运算符^，当两个数相同时，返回0，不同时返回1
3. 所以我们可以先将两个数异或，然后计算其中数字为1的个数，并累加起来，就是所求的结果。注意这里还需要使用到位运算符，复习左移和右移的区别。

## 代码
```
/**
 * @param {number} x
 * @param {number} y
 * @return {number}
 */
var hammingDistance = function(x, y) {
    var exc = x ^ y, res = 0;
    while(exc > 0){
        res += exc & 1;
        exc = exc >> 1;
    }
    return res;
};
```
