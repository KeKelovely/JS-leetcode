[Integer to Roman](https://leetcode.com/problems/integer-to-roman/description/)
### 问题描述
Given an integer, convert it to a roman numeral.

Input is guaranteed to be within the range from 1 to 3999.
### 解法
1. 阿拉伯数字转换为罗马数字，较简单的做法是列举出罗马数字对应的所有可能情形，然后利用贪心算法求解（每次总是转化最大的数，这样就能得到对应的唯一解）
### 源码
```
/**
 * @param {number} num
 * @return {string}
 */
var intToRoman = function(num) {
        var target = new String(),
            roman = ["M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"],
            values = [1000,900,500,400,100,90,50,40,10,9,5,4,1];
        for (var i = 0; num !== 0; i++){
            while (num >= values[i]){
                num = num - values[i];
                target = target + roman[i];
            }
        }
        return target;
};
```
### 运行时间

3999 / 3999 test cases passed.

Status: Accepted

Runtime: 156 ms

Your runtime beats 100.00 % of javascript submissions.
