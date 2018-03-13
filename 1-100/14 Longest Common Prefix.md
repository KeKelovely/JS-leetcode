
[Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/description/)

### 问题描述
Write a function to find the longest common prefix string amongst an array of strings.

### 解法描述
1. 正确理解题意：这里的最长公共子序列是对数字中的每一个元素而言的！即找出每一个元素共有的、最长的子序列
2. 最简单的做法是使用JS自带的sort()方法，排序后最长公共子序列只需要在strs[0]和strs[length-1]中寻找，剩下的就是一个简单的遍历问题
3. 注意处理字符串为空的情形

### 源码
```
/**
 * @param {string[]} strs
 * @return {string}
 */
var longestCommonPrefix = function(strs) {
            var target = new Array();
            target = "";
            if (strs.length !== 0){
                strs.sort();
                var max = strs.length - 1;
                var imax = strs[0].length;
                for (var i = 0; i < imax; i++){
                        if (strs[0][i] === strs[max][i]){
                            target = target + strs[0][i];                            
                        }else if (strs[0][i] !== strs[max][i]){
                            break;
                        }
                }
        }
        return target;
};
```
### 时间
117 / 117 test cases passed.

Status: Accepted

Runtime: 60 ms

Your runtime beats 100.00 % of javascript submissions.
