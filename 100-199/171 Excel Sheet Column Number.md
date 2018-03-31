[Excel Sheet Column Number](https://leetcode.com/problems/excel-sheet-column-number/description/)
### 问题描述
Related to question Excel Sheet Column Title

Given a column title as appear in an Excel sheet, return its corresponding column number.

For example:
```
    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
```
### 解法描述
1. 与Excel Sheet Column Title类似的思路，找规律，然后使用JavaScript自带的字符串与ASCII码的转换方法求解即可

### 源码
```
/**
 * @param {string} s
 * @return {number}
 */
var titleToNumber = function(s) {
            var res = 0;
            for (let i = 0; i < s.length; i++){
                res = res * 26 + s[i].charCodeAt() - 65 + 1;
            }
            return res;
};
```
### 运行时间

1000 / 1000 test cases passed.

Status: Accepted

Runtime: 80 ms

Your runtime beats 74.30 % of javascript submissions
