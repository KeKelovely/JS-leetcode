# 问题
[CLICK ME](https://leetcode.com/problems/binary-number-with-alternating-bits/description/)

# 解法

1. 本题首先将输入的数字转换为二进制数，然后要求判断这个二进制数是否每相邻位都不相同，如是，则返回true，反之为false
2. 首先，在JavaScript中将数字转换成二进制，可以使用_variable.toString(2)，将数字转换为二进制表示的字符串，至于判断相邻位是否相等就很简单了

# 代码
```
/**
 * @param {number} n
 * @return {boolean}
 */
var hasAlternatingBits = function(n) {
    var s = n.toString(2)
    for (var i = 1; i < s.length; i++) {
        if (s[i-1] == s[i]) {
            return false
        }
    }
    return true
};
```
