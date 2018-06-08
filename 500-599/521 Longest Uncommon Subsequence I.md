# 问题描述

[Click me](https://leetcode.com/problems/longest-uncommon-subsequence-i/description/)

# 解法

1. emmmm...只要两个字符串不相等，那最大的不同公共子序列长度就是这两个字符串里面长的那个家伙嘛！（因为每个字符串也是它自身的子序列）
2. 所以就一句话解决233

# Code
```
/**
 * @param {string} a
 * @param {string} b
 * @return {number}
 */
var findLUSlength = function(a, b) {
    return a == b?(-1):(Math.max(a.length, b.length)); 
};
```
