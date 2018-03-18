[Length of Last Word](https://leetcode.com/problems/length-of-last-word/description/)

### 问题描述
Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length of last word in the string.

If the last word does not exist, return 0.

Note: A word is defined as a character sequence consists of non-space characters only.

Example:
```
Input: "Hello World"
Output: 5
```

### 解法
1. 由于是找最后一个单词，所以从“尾”到“头”遍历即可。
- 遇到空格" "，跳过，继续向前，换言之就是找到第一个**不是空格**的单词
- 跳过前面的所有空格之后，遇到的第一个也就是最后一个单词，（因为我们是从尾巴到头遍历），然后count计数即可

> 这里很想吐槽，为什么"a "也可以算一个单词...单词后还有空格不正说明单词不存在吗？为什么还要算一个单词要求output为1，无法理解...

### 源码
```
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLastWord = function(s) {
        var tail = s.length - 1,
            count = 0;
        while (tail >=0 && s[tail] === ' ') tail--;
        while (tail >=0 && s[tail] !== ' '){
            tail--;
            count++;
        }
        return count;
};
```

### 运行时间

59 / 59 test cases passed.

Status: Accepted

Runtime: 48 ms

Your runtime beats 100.00 % of javascript submissions.
