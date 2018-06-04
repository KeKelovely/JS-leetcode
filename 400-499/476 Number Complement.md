# 问题描述
Given a positive integer, output its complement number. The complement strategy is to flip the bits of its binary representation.

Note:
The given integer is guaranteed to fit within the range of a 32-bit signed integer.
You could assume no leading zero bit in the integer’s binary representation.
Example 1:

```
Input: 5
Output: 2
Explanation: The binary representation of 5 is 101 (no leading zero bits), and its complement is 010. So you need to output 2.
```

Example 2:
```
Input: 1
Output: 0
Explanation: The binary representation of 1 is 1 (no leading zero bits), and its complement is 0. So you need to output 0.
```
# 解法

1. 给一个正整数，返回它的complement number，是指一个数的二进制表示形式取反的结果，如5的二进制是101，取反结果为010
2. 第一印象可能是直接对5取反，即~5，但32位二进制数位运算的结果是-6，（因为前面默认补上了0），所以这样做是行不通的
3. 所以，正确的做法是，对101和111异或，结果即为010，而前面的位数均为0，异或结果为0，就是0...0101 ^ 0...0111，结果就是我们所求的0...0010，省略前面的0，结果即为010
4. 现在的问题就是如何找出0...0111，这个数的特点是，除了原数二进制位以外，其余数均为0，剩下位均为1
5. 然后使用左移、右移位运算符，找出我们需要的3位即可

# 代码

```
/**
 * @param {number} num
 * @return {number}
 */
var findComplement = function(num) {
    var count = ~0,
        tmp = num;
    while (tmp > 0){
        count = count << 1;
        tmp = tmp >> 1;
    }
    return num ^ (~count);
};
```

