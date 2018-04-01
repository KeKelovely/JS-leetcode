[Isomorphic Strings](https://leetcode.com/problems/isomorphic-strings/description/)
### 问题描述
Given two strings s and t, determine if they are isomorphic.

Two strings are isomorphic if the characters in s can be replaced to get t.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character but a character may map to itself.

For example,
```
Given "egg", "add", return true.

Given "foo", "bar", return false.

Given "paper", "title", return true.
```

Note:
You may assume both s and t have the same length.

### 解法描述
1. “同构字符串匹配”问题，嘛，最简单的做法是使用Hash Table实现，在JavaScript中，Object允许将字符串作为键，从而建立字符串和数字之间的映射关系，而
Array继承自Object类型，因此直接使用数组即可实现一个类似的Hash Table，注意这时数组的下标就是单个的字符串啦
2. 然后逐个进行比较，如果出现不相等则返回false

### 源码
```
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isIsomorphic = function(s, t) {
    var m1 = new Array(),
        m2 = new Array();
    for (var i = 0; i < s.length; i++){
        if ( m1[s[i]] !== m2[t[i]] ) return false;
        m1[s[i]] = i+1;
        m2[t[i]] = i+1;
    }
    return true;
};
```
### 运行时间


30 / 30 test cases passed.

Status: Accepted

Runtime: 64 ms

Your runtime beats 95.20 % of javascript submissions.
