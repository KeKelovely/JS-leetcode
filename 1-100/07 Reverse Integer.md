[Reverse Integer](https://leetcode.com/problems/reverse-integer/description/)

### 问题描述
Given a 32-bit signed integer, reverse digits of an integer.

1. 翻转数字，每次使用%运算符得到原数的尾数，在转换过程中每次乘以10再加上新的尾数（初始为0），最后就能得到结果
2. 注意处理数字溢出的情况：
- JavaScript中的数字都是64位，且不区分浮点数与整数（**JS中只有一种数类型，就是Number**），也不存在int或float的强制类型转换符，但是32位的整数可以通过位运算符（|0,即与0作或运算）的方法得到（因为JS是将原数转换成32位再进行位运算，然后再转换为64位并输出）

```
var reverse = function(x) {
            var nums = 0;
            while (x != 0){
                var dx = x % 10;
                var newnums = nums * 10 + dx;
                if  (((newnums - dx)|0) / 10 !== nums){
                    return 0;
                }
                nums = newnums;
                x = (x-dx) / 10;
        }
            return nums;
};
```
