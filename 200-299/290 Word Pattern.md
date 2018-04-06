[Word Pattern](https://leetcode.com/problems/word-pattern/description/)

### 问题描述
Given a pattern and a string str, find if str follows the same pattern.

Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty word in str.

Examples:
pattern = "abba", str = "dog cat cat dog" should return true.
pattern = "abba", str = "dog cat cat fish" should return false.
pattern = "aaaa", str = "dog cat cat dog" should return false.
pattern = "abba", str = "dog dog dog dog" should return false.
Notes:
You may assume pattern contains only lowercase letters, and str contains lowercase letters separated by a single space.

### 解法描述
1. 和之前的一题：[Isomorphic Strings](https://github.com/KeKelovely/LeetCode-Solutions/blob/master/200-299/205%20Isomorphic%20Strings.md)几乎一模一样
2. 相当于进行的是一个字符串的基于位置的匹配，那么思路还是使用Hash表来做，建立每个String和数字之间的映射，然后依次比较即可。
3. 注意要先将字符串转换为数组，使用的是split()和slice()方法
### 源码描述
```
/**
 * @param {string} pattern
 * @param {string} str
 * @return {boolean}
 */
var wordPattern = function(pattern, str) {
	var p1 = pattern.split(""),
		s1 = str.split(" ");
	var pattern = new Array(),
		str = new Array();
	if (p1.length !== s1.length){
		return false;
	}
	for (var i = 0; i < p1.length; i++){
		if (pattern[p1[i]] !== str[s1[i]])	return false;
		pattern[p1[i]] = i+1;
		str[s1[i]] = i+1;
	}
	return true;
};
```
