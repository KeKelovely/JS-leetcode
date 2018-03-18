[70. Climbing Stairs](https://leetcode.com/problems/climbing-stairs/description/)

### 问题描述
You are climbing a stair case. It takes n steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

Note: Given n will be a positive integer.


Example 1:
```
Input: 2
Output:  2
Explanation:  There are two ways to climb to the top.

1. 1 step + 1 step
2. 2 steps
```
Example 2:
```
Input: 3
Output:  3
Explanation:  There are three ways to climb to the top.

1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```

### 解法
1. 由于只要求输出总数，所以找一下规律就发现这是个斐波那契数问题..
2. 然后基本操作，直接迭代循环实现即可。注意初始条件为1。
3. 这个数列最后应该是：1,2,3,5,8,13,21……

### 源码
```
/**
 * @param {number} n
 * @return {number}
 */
var climbStairs = function(n) {
        if (n === 1){
            return 1;
        }
        var onestep = 1,
            twostep = 1,
            result = 0;
        for (var i = 2; i <= n; i++){
            result = onestep + twostep;
            onestep = twostep;
            twostep = result;
        }
        return result;
};
```
### 时间


45 / 45 test cases passed.

Status: Accepted

Runtime: 56 ms

Your runtime beats 91.63 % of javascript submissions.
