# 问题
[CLICK ME](https://leetcode.com/problems/repeated-string-match/description/)

# 解法
1. 本题要求出字符串A重复多少次后，字符串B才构成字符串A的子串，返回次数
2. 判断是否为子串可以使用indexOf()方法实现，返回-1表示没有找到
3. 然后逐个判断，首先重复叠加字符串A，当A的长度大于B的长度时，记录下此时的次数，判断是否构成子串，如果不是，则继续添加一次A，再判断，如果没有则返回-1
（因为再重复下去结果是一样的，只需要判断两次就可以）

# 代码
```
/**
 * @param {string} A
 * @param {string} B
 * @return {number}
 */
var repeatedStringMatch = function(A, B) {
    var tmp = A
    var count = 1
    while (tmp.length < B.length) {
        tmp += A
        count++
    }
    // check whether A is substring of B in this count
    if (tmp.indexOf(B) != -1) {
        return count
    }else {
        tmp += A
        return tmp.indexOf(B) == -1 ? (-1):(count + 1)
    } 
};
```
