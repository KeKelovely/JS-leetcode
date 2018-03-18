[Count and Say](https://leetcode.com/problems/count-and-say/description/)

### 问题描述
The count-and-say sequence is the sequence of integers with the first five terms as following:
```
1.     1
2.     11
3.     21
4.     1211
5.     111221
1 is read off as "one 1" or 11.
11 is read off as "two 1s" or 21.
21 is read off as "one 2, then one 1" or 1211.
```
Given an integer n, generate the nth term of the count-and-say sequence.

Note: Each term of the sequence of integers will be represented as a string.
```
Example 1:

Input: 1
Output: "1"
Example 2:

Input: 4
Output: "1211"
```
### 问题解法

1. 题目意思就是，返回上一个字符串中的每一个字符的个数
2. 比如，n=1，字符串为1，那么n=2时，字符串为11（也就是“一个一”），以此类推
3. 用一个计数器count来“计数”，使用toString()方法将Number类型转换为String类型
> 这里的重点有二，一是理解toString()方法将number转换为string，二是使用count来合理计数，同样是注意循环的起始和次数，补充一点，使用+号来连接字符串

### 源码
```
/**
 * @param {number} n
 * @return {string}
 */
var countAndSay = function(n) {
        var s = "1";
        for (var i = 1; i < n; i++){
            var count = 1,
                tmpstr = "";
            for (var j = 1; j < s.length; j++){
                if (s[j] === s[j-1]){
                    count++;
                }else{
                    tmpstr = tmpstr + count.toString() + s[j-1];
                    count = 1;
                }
            }
            s = tmpstr + count.toString() + s[s.length-1];
        }
    return s;
};
```

### 运行时间

18 / 18 test cases passed.

Status: Accepted

Runtime: 60 ms

Your runtime beats 94.86 % of javascript submissions.
