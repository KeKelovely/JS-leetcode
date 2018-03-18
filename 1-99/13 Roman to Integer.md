[Roman to Integer](https://leetcode.com/problems/roman-to-integer/description/)
### 问题描述
Given a roman numeral, convert it to an integer.

Input is guaranteed to be within the range from 1 to 3999.
### 解法
1. 罗马数字与阿拉伯数字的转换关系：[点击这里](http://blog.csdn.net/wzy_1988/article/details/17057929)
2. 单个字符转换显然通过switch()实现
3. 转换规则（仅限于3999以内）
- 从前向后遍历罗马数字
- 如果某一个数比前一个数小，则加上该数，反之，减去前一个数的两倍然后加上该数

> 本质上还是一个数学游戏

### 源码实现
```
/**
 * @param {string} s
 * @return {number}
 */
var romanToInt = function(s) {
            function convert(c){
                var strdata = 0;
                 switch (c){
                    case 'I':
                        strdata = 1;
                        break;
                    case 'V':
                        strdata = 5;
                        break;
                    case 'X':
                        strdata = 10;
                        break;
                    case 'L':
                        strdata = 50;
                        break;
                    case 'C':
                        strdata = 100;
                        break;
                    case 'D':
                        strdata = 500;
                        break;
                    case 'M':
                        strdata = 1000;
                        break;
                }
                return strdata;
            }
        var number = convert(s[0]);
        for (var i = 1; i < s.length; i++){
                var c1 = convert(s[i-1]),
                    c2 = convert(s[i]);
                if (c1 < c2){
                    number = number + c2 - 2 * c1;
                }
                if (c1 >= c2){
                    number = number + c2;
                }
        }
       return number;
};
```

### 运行时间


3999 / 3999 test cases passed.

Status: Accepted

Runtime: 152 ms

Your runtime beats 100.00 % of javascript submissions.
