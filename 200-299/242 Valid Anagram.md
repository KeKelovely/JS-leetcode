[Valid Anagram](https://leetcode.com/problems/valid-anagram/description/)

### 问题描述
Given two strings s and t, write a function to determine if t is an anagram of s.

For example,
s = "anagram", t = "nagaram", return true.
s = "rat", t = "car", return false.

Note:
You may assume the string contains only lowercase alphabets.

### 解法描述
1. 重构字符串问题，前面有几题也涉及到了字符串比较判断的操作，这里还是一如既往的使用Hash结构（JS中的Array类型），建立字符与数字之间的键-值对关系
2. 剩下的就是基本操作...首先把s处理完，然后再遍历t，遇到相同的字符时则减去1，遍历完后如果整个Array为0，说明这两个字符串是重构的

### 源码实现
```
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isAnagram = function(s,t) {
    var hash = new Array();
    if (s.length !== t.length) return false;
    for (var i = 0; i < s.length; i++){
    	if (s[i] in hash){
    		hash[s[i]]++;
    	}else{
    		hash[s[i]] = 1;
    	}
    }
    for (var j = 0; j < t.length; j++){
    	if (t[j] in hash){
    		hash[t[j]]--;
    	}
    }
    for (var k = 0; k < s.length; k++){
    	if (hash[s[k]] !== 0){
    		return false;
    		break;
    	}
    }
    return true;
};
```
