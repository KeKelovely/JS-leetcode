[Implement strStr()](https://leetcode.com/problems/implement-strstr/description/)

### 问题描述
Implement strStr().

Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.
```
Example 1:

Input: haystack = "hello", needle = "ll"
Output: 2
Example 2:

Input: haystack = "aaaaa", needle = "bba"
Output: -1
```
### 解法：

1. 找出目标字符串中某字符串第一次出现的位置
2. 这题最简单粗暴的解法就是使用arr.indexOf()方法实现

> 想一想，如果不用indexOf()，要如何实现呢？如何确保在后续遇到已经遍历过的元素时将其忽略掉？
```
/**
 * @param {string} haystack
 * @param {string} needle
 * @return {number}
 */
var strStr = function(haystack, needle) {
        if (haystack.indexOf(needle) > -1){
            return haystack.indexOf(needle);
        }else{
            return -1;
        }
};
```
### 运行时间
~~这种实现方法好像也没必要测试时间...~~
下次写一个原生indexOf实现再来测试一下效果
