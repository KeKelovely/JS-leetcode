[Sum of Two Integers](https://leetcode.com/problems/sum-of-two-integers/description/)
### 问题描述
Calculate the sum of two integers a and b, but you are not allowed to use the operator + and -.

Example:
Given a = 1 and b = 2, return 3.
### 解法描述
1. 实现加法运算，要求不能用+/-运算符
2. 这里只能通过位运算的方式来实现，那么就去寻找位运算符与实际的加法运算之间的关系：a & b可以得到进位的结果(这里的进位少一位)，a ^ b可以得到两数相加的结果，然后将进位向前进一位，重复直到b为0，说明此时不存在进位，直接相加输出即可。
3. 核心要点就是a & b来求进位，a ^ b来求两数相加的结果（注意这里的a和b都是采用的二进制方式的计算）
### 源码
```
/**
 * @param {number} a
 * @param {number} b
 * @return {number}
 */
var getSum = function(a, b) {
    let carry = 0;
    while(b){
        carry = a & b;
        a = a ^ b;
        b = carry << 1;
    }
    return a;
};
```
