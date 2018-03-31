[Excel Sheet Column Title](https://leetcode.com/problems/excel-sheet-column-title/description/)

### 问题描述
Given a positive integer, return its corresponding column title as appear in an Excel sheet.

For example:
```
    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 
```

### 解法描述
1. 本质上就是一个找规律的题。。利用String.fromCharCode()方法实现ASCII码向字符的转换，然后依次除以26就行了，找规律就行..不赘述

### 源码实现
```
/**
 * @param {number} n
 * @return {string}
 */
var convertToTitle = function(n) {
            var res = new Array();
            while (n>0){
                n--;
                res.unshift(String.fromCharCode(65 + n % 26));
                n = parseInt(n/26);
            }
            return res.join('');
};
```
### 运行时间

18 / 18 test cases passed.

Status: Accepted

Runtime: 68 ms

Your runtime beats 53.01 % of javascript submissions.
