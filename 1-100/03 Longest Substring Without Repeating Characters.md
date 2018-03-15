[Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)
### 问题描述
Given a string, find the length of the longest substring without repeating characters.
```
Examples:

Given "abcabcbb", the answer is "abc", which the length is 3.

Given "bbbbb", the answer is "b", with the length of 1.

Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```
### 解法
1. 从头开始遍历整个字符串，挨个搜索即可，分为两种情况
- 在当前搜索区间内，没有碰到重复使用过的元素
- 在当前区间内遇到了重复元素
2. 由于是统计字符串长度，因此用i和start来表示**当前位置**和**起始位置**，已经遍历过的元素存放在usedchar对象中，usedchar总是记录每个元素最近出现的位置
- 比如对'abc'来说，当i=3时，usedchar应当为：
```
var usedchar = {
      'a' = 0;
      'b' = 1;
      'c' = 2;
};
```
- 重复：修改start的位置，从此前重复位置的后一个开始算起
- 不重复：比较最大长度
> 纯文字描述很繁琐，此处画个图就很好理解了，分别用i和start记录位置，然后就是分类讨论，寻找分类讨论的条件就可以了！
### 源码
```
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
            var start = 0,
                maxLength = 0,
                usedChar = {};
            for (var i = 0, imax = s.length; i < imax; i++){
                if (s[i] in usedChar && start <= usedChar[s[i]]){
                    start = usedChar[s[i]]+1;
                }
                else{
                    maxLength = Math.max(maxLength, i - start + 1);
                }
                usedChar[s[i]] = i;
            }
            return maxLength;
};
```
### 运行时间

983 / 983 test cases passed.

Status: Accepted

Runtime: 112 ms

Your runtime beats 83.36 % of javascript submissions.
