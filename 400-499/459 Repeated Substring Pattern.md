# 问题
Given a non-empty string check if it can be constructed by taking a substring of it and appending multiple copies of the substring together. You may assume the given string consists of lowercase English letters only and its length will not exceed 10000.
```
Example 1:
Input: "abab"

Output: True
```
Explanation: It's the substring "ab" twice.
```
Example 2:
Input: "aba"
Output: False
```
```
Example 3:
Input: "abcabcabcabc"

Output: True
```
Explanation: It's the substring "abc" four times. (And the substring "abcabc" twice.)

# 解法

## 常规遍历
逐个判断，首先从s[0]开始，依次判断s[1]、s[2]...s[m-1]（m=s.length）与s[0]是否相等，若相等，返回true，若不等，转而判断s[0]~s[1]构成的子串
然后判断s[0]~s[1]构成的子串是否与s[2]~s[3]构成的子串相等，若相等，继续向后遍历，不等，则转而判断长度为3的子串
由定义可知，最多只需要判断原字符串的一半即可

### 代码
```
/**
 * @param {string} s
 * @return {boolean}
 */
var repeatedSubstringPattern = function(s) {
    var m = s.length;
    for (var i = 1; i < m/2+1; i++){
        for (var j = 0; j < m-i; j++){
            if(s[j] !== s[j+i]) break;
            if(m % i === 0 && j === m-i-1) return true;
        }
    }
    return false;
};
```

## KMP
