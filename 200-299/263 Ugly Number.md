[Ugly Number](https://leetcode.com/problems/ugly-number/description/)

### 问题描述
Write a program to check whether a given number is an ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. For example, 6, 8 are ugly while 14 is not ugly since it includes another prime factor 7.

Note:

1 is typically treated as an ugly number.
Input is within the 32-bit signed integer range.

### 解法描述
1. 如果一个数的质因子只有2,3,5，那么这就是一个丑陋数。其实这里的描述还不太准确，丑陋数的所有因子除了1之外2、3、5，所以直接除除除找答案就行了...
2. 所以本质上还是一个数学题而不是一个算法题。。

### 源码
```
/**
 * @param {number} num
 * @return {boolean}
 */
var isUgly = function(num) {
    while (num >= 2){
        if (num % 2 === 0) num = parseInt(num/2);
        else if (num % 3 === 0) num = parseInt(num/3);
        else if (num % 5 === 0) num = parseInt(num/5);
        else return false;
    }
    if (num === 1){
        return true;
    }else{
        return false;
    }
};
```
