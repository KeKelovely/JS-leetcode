# 问题描述

[Click me](https://leetcode.com/problems/longest-uncommon-subsequence-ii/description/)

# 解法

1. 与上一题521类似，本题只需找出最长的LUS即可。这里首先将数组根据字符串的长度按递减排序，得到长度依次递减的字符串数组
2. 然后依次遍历strs，如果后面存在比当前元素还要长的字符串，那么判断前者是否为前者的子串，如果是，则向后继续判断，直到所有的元素都满足存在这一公共子串，说明并不存在LUS，返回-1
3. 反之，如果当前元素不是后面元素中的substring，则直接返回当前元素的长度即可。
4. 本题与521题的解法类似，只需要写一个判断是否为substring的函数即可，然后在遍历时我们只考虑更长的元素

# Code
```
/**
 * @param {string[]} strs
 * @return {number}
 */
var findLUSlength = function(strs) {
    strs.sort((s1,s2)=>s2.length-s1.length);
    // the strs are [long, mid, ..., short]
    for (var i in strs) {
        var hasCS = false;
        for (var j = 0; j < strs.length && strs[j].length >= strs[i].length; j++){
            if (i == j) continue;
            if (isSubString(strs[j], strs[i])) {
                hasCS = true;
                break;
            }
        }
        if (hasCS == false) {
            break;
        }
    }
    return hasCS == true? -1 : strs[i].length;
};

var isSubString = function(s1,s2) {
    // return true if s2 is substring of s1
    if (s1.length == s2.length) {
        return s1 == s2 ? true : false;
    }else {
        var i = 0,
            j = 0;
        while ( j < s2.length ) {
            var target = s2[j];
            while (i < s1.length && s1[i] != target) {
                i++;
            }
            if (i == s1.length) return false;
            i++;
            j++;
        }
        return true;
    }
}
```
