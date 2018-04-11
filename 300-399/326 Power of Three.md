[Power of Three](https://leetcode.com/problems/power-of-three/description/)
### 问题描述
Given an integer, write a function to determine if it is a power of three.

Follow up:
Could you do it without using any loop / recursion?

### 解法描述
1. 判断一个数是否为3的幂，要求不能使用任何的loop or recursion
2. 这里直接用一个取巧的方法...本题的最大整数限制在32位整数内，而32bit integers最大的也就是3^19，所以直接用3^19来整除我们要判断的数，如果结果为0，说明就是3的幂
3. 本质上还是一个数学问题..

### 源码描述
```
/**
 * @param {number} n
 * @return {boolean}
 */
var isPowerOfThree = function(n) {
    var maxPow_of_three = Math.pow(3,19);
    if (n > 0 && maxPow_of_three % n == 0) return true;
    else return false;
};
```
