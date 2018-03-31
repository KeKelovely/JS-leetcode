[Single Number](https://leetcode.com/problems/single-number/description/)

### 问题描述
Given an array of integers, every element appears twice except for one. Find that single one.

Note:
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

### 解法
1. 找出数组当中的单身狗，也就是有的数字是成对相同，只有一个单独列出来的不同，那么可以联想到位运算符中的亦或运算符"^"
2. 如果两个数相同，x=y，那么 x ^ y = 0,如果将数组中所有元素依次作" ^ "运算，成对相同的数字亦或结果均为0（亦或运算符合交换律），剩下的那个就是我们要找的单身狗

### 源码实现
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
    var num = 0;
    for (var i = 0; i < nums.length; i++){
        num = num ^ nums[i];
    }
    return num;
};
```
### 运行时间

15 / 15 test cases passed.

Status: Accepted

Runtime: 56 ms

Your runtime beats 98.58 % of javascript submissions.
