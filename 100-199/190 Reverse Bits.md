[Reverse Bits](https://leetcode.com/problems/reverse-bits/description/)

### 问题描述
Reverse bits of a given 32 bits unsigned integer.

For example, given input 43261596 (represented in binary as 00000010100101000001111010011100), return 964176192 (represented in binary as 00111001011110000010100101000000).

Follow up:
If this function is called many times, how would you optimize it?

Related problem: Reverse Integer

### 解法描述
1. 反转一个32位无符号的整数
2. 利用位运算实现。利用result来保存结果，将result右移一位腾出空间存放位数，然后result加上n&1的结果（取尾数），然后n依次右移一位
3. 最后注意JavaScript会默认将result当作有符号的整数，因此需要加上无符号右移运算使得result变成无符号整数

### 源码
```
/**
 * @param {number} n - a positive integer
 * @return {number} - a positive integer
 */
var reverseBits = function(n) {
    var result = 0;
    for (var i = 0; i < 32; i++){
        result <<= 1;
        result += n & 1;
        n >>= 1;
    }
    result >>>= 0;
    return result;
};
```
### 运行时间
600 / 600 test cases passed.

Status: Accepted

Runtime: 88 ms

Your runtime beats 63.53 % of javascript submissions.
