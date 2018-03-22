[Valid Palindrome](https://leetcode.com/problems/valid-palindrome/description/)
### 问题描述
Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

For example,
"A man, a plan, a canal: Panama" is a palindrome.
"race a car" is not a palindrome.

Note:
Have you consider that the string might be empty? This is a good question to ask during an interview.

For the purpose of this problem, we define empty string as valid palindrome.


### 解法：
1. 选择两个指针，依次指向字符串的头和尾，然后迭代循环，到两指针相等时循环结束
2. 如果中间遇到非字母or数字，则跳过，若遇到字母，则比较是否相等，注意使用toLowerCase()方法转换大小写


### 源码
```
/**
 * @param {string} s
 * @return {boolean}
 */
var isPalindrome = function(s) {
            var left = 0,
                right = s.length-1,
                cleft = null,
                cright = null;
            while (left < right){
                cleft = s[left];
                cright = s[right];
                if ( !isString(cleft) ){
                    left++;
                }else if ( !isString(cright) ){
                    right--;
                }else{
                    if (cleft.toLowerCase() !== cright.toLowerCase()){
                        return false;
                    }
                    left++;
                    right--
                }
            }
            return true;
};
var isString = function(c){
        if (c >= 'a' && c <= 'z'){
            return true;
        }
        if (c >= 'A' && c<= 'Z'){
            return true;
        }
        if (c >= '0' && c <= '9'){
            return true;
        }
        return false;
};
```
### 运行时间

476 / 476 test cases passed.

Status: Accepted

Runtime: 84 ms

Your runtime beats 72.29 % of javascript submissions.
