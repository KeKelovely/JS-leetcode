# 9 Palindrome Number

[Palindrome Number-回文数](https://leetcode.com/problems/palindrome-number/description/)
### 问题描述
Determine whether an integer is a palindrome. Do this without extra space.

1. 可以使用字符串方法（但本题不允许）
2. 使用与7 - Reverse Number类似的方法，判断翻转后的数字是否相等
3. 注意处理数字是否溢出（同样用到位操作符）

> 总结：数字翻转/回文问题，除了使用字符串以外，可以“互逆式”地乘10除10从而得到结果，即**反复**除10得尾数，**反复**乘10得到翻转后的数

~~当然这么做有点偷懒，不过运行效率还行~~

```
/**
 * @param {number} x
 * @return {boolean}
 */
var isPalindrome = function(x) {
            if (x < 0) {return false;}
            var num = 0,
                copyx = x;
            while (x != 0){
                tail = x % 10;
                newnum = num * 10 + tail;
                num = newnum;
                x = (x - tail) / 10;
            }
            num = num|0;
            return (copyx === num);
};
```

### 运行时间
11507 / 11507 test cases passed.

Status: Accepted

Runtime: 300 ms

Your runtime beats 99.90 % of javascript submissions.
