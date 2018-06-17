# 问题

[Click me](https://leetcode.com/problems/student-attendance-record-i/description/)

# 解法描述
1. 本题就是判断字符串中各字母出现的次数，再与题目所给的条件进行比较
2. 题目一比较简单，直接对整个字符串按序遍历，当不满足所给条件时返回false即可
# CODE

```
/**
 * @param {string} s
 * @return {boolean}
 */
var checkRecord = function(s) {
    var countA = 0;
    for (var i = 0; i < s.length; i++) {
        if (s[i] == 'A') {
            countA++;
            if (countA > 1) return false;
        }else if (s[i] == 'L') {
            if (s[i+1] == 'L' && s[i+2] == 'L') return false;
        }
    }
    return true;
};
```
