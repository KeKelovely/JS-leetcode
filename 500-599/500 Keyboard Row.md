# 问题描述
Given a List of words, return the words that can be typed using letters of alphabet on only one row's of American keyboard like the image below.


American keyboard

![IMG](https://leetcode.com/static/images/problemset/keyboard.png)

Example 1:
```
Input: ["Hello", "Alaska", "Dad", "Peace"]
Output: ["Alaska", "Dad"]
```

Note:
You may use one character in the keyboard more than once.
You may assume the input string will only contain letters of alphabet.

# 解法
1. 找出数组中可以被键盘上一行所打出来的字符串
2. 很简单的题，其实三行做下来都是重复操作，熟练运用indexOf()方法即可
3. 注意做一个简单的函数封装，让代码更好看

# 代码
```
/**
 * @param {string[]} words
 * @return {string[]}
 */
var findWords = function(words) {
    var alphabets = ['qwertyuiop','asdfghjkl','zxcvbnm'],
        res = [];
    for (var i in words){
        for (var j in alphabets){
            if (searchWords(alphabets[j],words[i])){
                res.push(words[i]);
            }
        }
    }
    return res;
};

var searchWords = function(list,s){
    s = s.toLowerCase();
    for (var k in s){
        if (list.indexOf(s[k]) === -1) return false;   
    }
    return true;
}
```
