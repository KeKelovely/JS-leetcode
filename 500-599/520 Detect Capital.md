# 问题描述

[Click me](https://leetcode.com/problems/detect-capital/description/)

# 解法

1. 读懂就会做..无脑分类讨论，注意单词长度为1时返回true，其他的情况逐个分析即可。

# Code

```
/**
 * @param {string} word
 * @return {boolean}
 */
var detectCapitalUse = function(word) {
        if (word.length == 1){
            return true;
        }
        // if first letter is lowercase
        if ( word[0] >='a' && word[0] <= 'z') {
            for (var i = 1; i < word.length; i++){
                if (word[i] >= 'A' && word[i] <= 'Z') return false;
            }
            return true;
        }
        // if first letter is uppercase
        if ( word[0] >= 'A' && word[0] <= 'Z') {
            // if second is also uppercase
            if ( word[1] >= 'A' && word[1] <= 'Z') {
                for (var j = 2; j < word.length; j++){
                    if (word[j] >= 'a' && word[j] <= 'z') return false;
                }
                return true;
            }
            // if second is lowercase
            if (word[1] >= 'a' && word[1] <= 'z') {
                for (var k = 2; k < word.length; k++){
                    if (word[k] >= 'A' && word[k] <= 'Z') return false;
                }
                return true;
            }
        }
};
```
