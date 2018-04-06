[Missing Number](https://leetcode.com/problems/missing-number/description/)
### 问题描述
Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array.

Example 1
```
Input: [3,0,1]
Output: 2
```
Example 2
```
Input: [9,6,4,2,3,5,7,0,1]
Output: 8
```
Note:
Your algorithm should run in linear runtime complexity. Could you implement it using only constant extra space complexity?

### 解法描述
1. 本题要求求出一个数组当中的missing number，简单的做法是直接求和，再与0~n的和作减法，减出来的差值就是我们所需要的missing number
### 源码描述
```
Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array.

Example 1

Input: [3,0,1]
Output: 2
Example 2

Input: [9,6,4,2,3,5,7,0,1]
Output: 8

Note:
Your algorithm should run in linear runtime complexity. Could you implement it using only constant extra space complexity?
```
