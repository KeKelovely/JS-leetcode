# 问题
Given a non-empty string check if it can be constructed by taking a substring of it and appending multiple copies of the substring together. You may assume the given string consists of lowercase English letters only and its length will not exceed 10000.
```
Example 1:
Input: "abab"

Output: True
```
Explanation: It's the substring "ab" twice.
```
Example 2:
Input: "aba"
Output: False
```
```
Example 3:
Input: "abcabcabcabc"

Output: True
```
Explanation: It's the substring "abc" four times. (And the substring "abcabc" twice.)

# 解法

## 常规遍历
逐个判断，首先从s[0]开始，依次判断s[1]、s[2]...s[m-1]（m=s.length）与s[0]是否相等，若相等，返回true，若不等，转而判断s[0]~s[1]构成的子串
然后判断s[0]~s[1]构成的子串是否与s[2]~s[3]构成的子串相等，若相等，继续向后遍历，不等，则转而判断长度为3的子串
由定义可知，最多只需要判断原字符串的一半即可

### 代码
```
/**
 * @param {string} s
 * @return {boolean}
 */
var repeatedSubstringPattern = function(s) {
    var m = s.length;
    for (var i = 1; i < m/2+1; i++){
        for (var j = 0; j < m-i; j++){
            if(s[j] !== s[j+i]) break;
            if(m % i === 0 && j === m-i-1) return true;
        }
    }
    return false;
};
```

## KMP

参考资料：[字符串匹配的KMP算法](http://www.ruanyifeng.com/blog/2013/05/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm.html)
简单来说，即利用KMP算法中的next数组（next数组记录了字符串前缀后缀中最长相同子串的长度），如果一个字符串可以被拆分成多个子字符串的组合，那么其next数组的最后一个数值必定为子字符串长度的倍数。
例如，对"abab"而言，其next数组为[0,0,1,2]，最后一个数2，必定为子字符串"ab"的长度的2的倍数。即长度为2的字符串出现了两次，那么前后缀中最长相同子串长度为2*(2-1) = 2
同理，对"abcabcabc"而言,长度为3的子字符串abc出现了三次，那么next数组的最后一个值为3*(3-1) = 6
总结下来，只要next数组的最后一个数是子字符串长度的倍数（且不能为0），那么这个字符串就一定是我们所求的结果。
所以，最后这个问题就归结为如何求一个字符串的next数组，具体算法可参考：[KMP算法](https://blog.csdn.net/starstar1992/article/details/54913261/)

### 参考代码
```
/**
 * @param {string} s
 * @return {boolean}
 */
var repeatedSubstringPattern = function(s) {
    var m = s.length,
        i = 1,
        j = 0,
        arr = Array.apply(null,Array(m+1)).map(function(item,i){
            return 0;
        });
    while( i < m ){
        if (s[i] === s[j]) arr[++i] = ++j;
        else if( j === 0 ) i++;
        else j = arr[j];
    }
    if (arr[m] && arr[m]%(m-arr[m])==0){
        return true;
    }else return false;
};
```
