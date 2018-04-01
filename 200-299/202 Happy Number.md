[Happy Number](https://leetcode.com/problems/happy-number/description/)

### 问题描述
Write an algorithm to determine if a number is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.
```
Example: 19 is a happy number

1^2 + 9^2 = 82
8^2 + 2^2 = 68
6^2 + 8^2 = 100
1^2 + 0^2 + 0^2 = 1
```
### 解法描述
1. 基本没有什么算法要求，就是一个数学trick，注意对非happynumber来说，一定会出现数字4（数学证明..），以此可作为循环终止条件，相应的，happynumber一定会有数字1

### 源码
```
/**
 * @param {number} n
 * @return {boolean}
 */
var isHappy = function(n) {
    while (n !== 1 && n !== 4){
        var tmp = 0;
        while (n){
            tmp += (n % 10) * (n % 10);
            n = parseInt(n/10);
        }
        n = tmp;
    }
    return n === 1;
};
```

### 运行时间

401 / 401 test cases passed.

Status: Accepted

Runtime: 68 ms

Your runtime beats 92.31 % of javascript submissions.
