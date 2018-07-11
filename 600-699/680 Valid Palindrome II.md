# 问题
[CLICK ME](https://leetcode.com/problems/valid-palindrome-ii/description/)

# 解法
1. 本题是回文字符串的加强版，要判断是否能够在至多删除一个字符的情况下，该字符串为回文字符串
2. 同样参考之前的想法，用头尾双指针来比较字符串是否相等，当遇到不等的字符串时，递归判断，要么是往后多一个字符，要么是往前进一个字符（都是跳过一个字符），然后继续判断


# 代码
```
/**
 * @param {string} s
 * @return {boolean}
 */
var validPalindrome = function(s) {
    return isPalindrome(s, 0, s.length-1, 0)
};

var isPalindrome = function(s, left, right, flag) {
    while (left < right) {
        if (s[left] == s[right]) {
            left++
            right--
        }else {
            if (flag == 1) return false
            flag = 1
            return isPalindrome(s, left+1, right, flag) || isPalindrome(s, left, right-1, flag)
        }
    }
    return true
}
```
