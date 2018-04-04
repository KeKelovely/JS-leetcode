[Add Digits](https://leetcode.com/problems/add-digits/description/)

### 问题描述
Given a non-negative integer num, repeatedly add all its digits until the result has only one digit.

For example:

Given num = 38, the process is like: 3 + 8 = 11, 1 + 1 = 2. Since 2 has only one digit, return it.

Follow up:
Could you do it without any loop/recursion in O(1) runtime?

### 解法描述
1. 如果不对数字本身进行递归或者除法取余等操作，而是要求O(1)的运行时间，那么本质上这就是一个奥数问题而不是一个算法问题...
2. 解法链接：https://en.wikipedia.org/wiki/Digital_root#Congruence_formula
3. 最后的结果其实是一个循环，即0 1 2 3 4 5 6 7 8 9 1 2 3 4 5 6 7 8 9，除了第一位0以外，其余每9位是一组

### 源码
```
/**
 * @param {number} num
 * @return {number}
 */
var addDigits = function(num) {
    return (num - 1) % 9 + 1;
};
```
