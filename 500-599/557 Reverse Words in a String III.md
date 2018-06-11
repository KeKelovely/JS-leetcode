# 问题描述

[Click me!](https://leetcode.com/problems/reverse-words-in-a-string-iii/description/)

# 解法描述

1. 比较简单，灵活使用字符串的split以及数组的join、reverse方法即可

# Code

```
/**
 * @param {string} s
 * @return {string}
 */
var reverseWords = function(s) {
    var arr = s.split(" "),
        res = [];
    for (var i in arr) {
        res[i] = reverseOneString(arr[i]);
    }
    return res.join(" ");
};

var reverseOneString = function(s) {
    return s.split("").reverse().join("");
}

reverseWords("Let's take LeetCode contest");
```
