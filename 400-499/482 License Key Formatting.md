
# 问题描述

[Click me!](https://leetcode.com/problems/license-key-formatting/description/)

# 解法

1. 本题需要对输入的字符串进行格式化。这里可以先做一个预处理，使用splite以及join等方法去掉字符串中的"-"，这样方便后续操作。
2. 然后需要**逆序**遍历字符串，因为正序来做需要区分不同的情况，分类讨论起来十分复杂（你试了就知道了233）
3. 每当遍历经过K个字母时，就添加上"-"符号，直到i = 0，即字符串到头为止，结束遍历即为所求。

# Code

```
/**
 * @param {string} S
 * @param {number} K
 * @return {string}
 */
var licenseKeyFormatting = function(S, K) {
    var str = S.split('-').join("").toUpperCase(),
        res = "";
    var i = str.length-1;
    while (i >= 0){
    	res = str[i] + res;
    	if ((str.length - i) % K == 0 && i != 0){
    		res = "-" + res;
    	}
    	i--;
    }
    return res;
};
```
