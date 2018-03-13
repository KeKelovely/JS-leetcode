[Valid Parentheses](https://leetcode.com/problems/valid-parentheses/description/)

### 问题描述
Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

The brackets must close in the correct order, "()" and "()[]{}" are all valid but "(]" and "([)]" are not.

### 解法
1. 这是一个字符串匹配问题，注意：**字符串匹配问题优先使用栈的数据结构来处理**

> JS中并没有特别地定义Stack，但是Array中提供了arr.pop()和arr.push()方法，实际上也是对Stack的一种实现

2. 匹配解法：
- 左符号：直接进栈（不需要涉及到匹配）
- 右符号：判断是否和栈顶元素相等，若相等则出栈，不等则返回false

### 源码

```
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
        strs = new Array();
        for (var i = 0; i < s.length; i++){
            if (( s[i] === "(" ) || ( s[i] === "[" ) || ( s[i] === "{" ))  {
                strs.push(s[i]);                
            }else if (( s[i] === ")" && strs[strs.length-1] === "(") 
                 || ( s[i] === "]" && strs[strs.length-1] === "[" )
                 || ( s[i] === "}" && strs[strs.length-1] === "{" ))  {
                strs.pop();                
            }else {
                return false;
            }
        } 
        if (strs.length === 0){
                return true;
            }else if (strs.length !== 0 ){
                return false;
            }
};
```

### 运行时间


73 / 73 test cases passed.

Status: Accepted

Runtime: 60 ms

Your runtime beats 100.00 % of javascript submissions.
