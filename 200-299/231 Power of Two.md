### 问题描述
Given an integer, write a function to determine if it is a power of two.
### 解法描述
1. 给一个整数，判断其是否为2的幂...这里我用了二进制的做法，如果一个数是2的幂，那么其二进制的形式一定可以写成"100...",即首位为1，其余位均为0
2. 然后使用toString(2)方法将整数转换为二进制形式的字符串，用indexOf()检索后续位中是否存在1，如果存在，返回false
### 源码
```
/**
 * @param {number} n
 * @return {boolean}
 */
var isPowerOfTwo = function(n) {
    if (n === 0) return false;
    var str = n.toString(2);
    if (str.substring(1,str.length).indexOf('1') !== -1)  return false;
    return true;
};
```
