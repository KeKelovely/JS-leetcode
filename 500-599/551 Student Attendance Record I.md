# 问题

[Click me](https://leetcode.com/problems/student-attendance-record-i/description/)

# 解法描述

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
