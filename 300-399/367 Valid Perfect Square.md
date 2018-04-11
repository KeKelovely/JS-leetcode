[Valid Perfect Square](https://leetcode.com/problems/valid-perfect-square/description/)
### 问题描述
Given a positive integer num, write a function which returns True if num is a perfect square else False.

Note: Do not use any built-in library function such as sqrt.

Example 1:
```
Input: 16
Returns: True
```
Example 2:
```
Input: 14
Returns: False
```

### 解法描述
1. 判断一个数是否是一个完全数，说白了也就是个数学问题，所有奇数构成的等差数列之和正好等于n^2(1 + 3 + 5 + 7 + ...)
2. 然后逐个判断验证即可，同样可以采用与二分查找类似的思路，从num/2开始判断，缩小查找范围，这里就不演示了

### 源码
```
/**
 * @param {number} num
 * @return {boolean}
 */
var isPerfectSquare = function(num) {
    let i = 1;
    while (num > 0){
        num -= i;
        i += 2;
    }
    if (num === 0){
        return true;
    }else {
        return false;
    }
};
```
