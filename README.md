# LeetCode By JavaScript
LeetCode Solutions (All By JavaScript!)
> [LeetCode](https://leetcode.com/)的个人Solutions汇总，全部使用JavaScript完成:satisfied:

> 目的：了解、掌握数据结构和算法，当然更重要的是学会如何用JS实现（如JS中的Hash Table、BST等），和JS结下更深的友谊:clap:

> 其他：做笔记备份的目的是方便以后复习和再学习，同时也看看以前写的算法是有多么傻x:shit:

#### [LeetCode地址](https://leetcode.com)
#### 如需中文,可=>[戳我访问LeetCode中文](https://leetcode-cn.com)

## 一、基本格式
0. 问题链接
……
1. 问题描述
……
2. 解法描述
……
3. 源码实现（确保Accpted无误）
```
//
```
4. 运行时间
……

## 二、Index目录引导

> 其中数字表示题目的顺序编号

### 1.运算基础（数字的基本运算、简单的求和等）
- 01 Two Sum ：两数之和
- 07 Reverse Integer：翻转整数
- 09 Palindrome Number：回文数
- 11 Container With Most Water：双指针搜索的典型例子
- 12 Integer to Roman： 将阿拉伯数字转换为罗马数字
- 38 Count and Say：计算并递归
- 53 Maximum Subarray: 求子数组的元素和的最大值，是分冶法的一个经典应用（Divide And Conquer）
- 70 Climbing Stairs：一个斐波那契数列的递归实现

### 2.数据结构（数组、链表、栈、队列）
- 02 Add Two Numbers：用链表实现两数求和
- 04 Median of Two Sorted Arrays：在两个已排序的数组间求中间值
- 20 Valid Parentheses：符号配对问题，本题虽然涉及到字符串，但实际上是用栈解决问题的经典例子
- 21 Merge Two Sorted Lists：合并两个已排序的链表
- 24 Swap Nodes in Pairs：交换链表中的一对节点
- 26 Remove Duplicates from Sorted Array：去掉已排序的数组中的重复元素，用双指针解决
- 27 Remove Element：去掉数组中指定的元素，用双指针解决
- 35 Search Insert Position：找到元素的插入位置，是Binary Search的典型应用
- 66 Plus One：链表运算
- 83 Remove Duplicates from Sorted List：去除链表中的重复元素
- 88 Merge Sorted Array：合并有序数组


### 3.字符串问题（回文字符串、子字符串等）
- 03 Longest Substring Without Repeating Characters：不含重复字符的最长子字符串
- 14 Longest Common Prefix：最长公共子序列问题
- 22 Generate Parentheses：输出所有可能的括号“配对”结果，考查带条件的搜索
- 28 Implement strStr：找出某个字符在字符串中第一次出现的位置，如果不用indexOf应如何实现
- 58 Length of Last Word： 最后一个单词的长度，考查对字符串的遍历

### 4.树问题（二叉树、二叉搜索树等）

### 5.高级算法（如动态规划等）
- 46 Permutations：全排列问题
- 47 Permutations：全排列问题2，考虑重复数字的情形

### 6.数学问题（如矩阵等）
- 48 Rotate Image：矩阵的旋转变换

## 三、一个栗子
---

# 2 Add Two Numbers
[Add Two Numbers](https://leetcode.com/problems/add-two-numbers/description/)
### 问题描述
  You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and 
each of their nodes contain a single digit. Add the two numbers and return it as a linked list.
  You may assume the two numbers do not contain any leading zero, except the number 0 itself.

1. 用链表形式完成两数相加的操作，注意这里的**限制条件**是两数的最高位相同（比如，不会存在千位数加百位数的情况，这是Add Two Numbers ②讨论的问题）
2. 解题
- 掌握用链表表示数据的方法（**亦是本题考查的重点**），即s.val/s.next的形式
- 注意分类讨论，主要是进位的情形，不进位则为0，进位则为1,
- 用一个新的链表来存储结果

```
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var addTwoNumbers = function(l1, l2) {
            var carry = 0;
            var s = new ListNode(0);
            var nums = new Array();
            while (l1 !== null || l2 !== null || carry){
                if (l1 !== null){
                    s.val = s.val + l1.val;
                    l1 = l1.next;
                }
                if (l2 !== null){
                    s.val = s.val + l2.val;
                    l2 = l2.next;
                }
                carry = parseInt(s.val/10);
                s.val = s.val % 10;
                nums.push(s.val);
                if (l1 !== null || l2 !== null || carry){
                    s.next = new ListNode(carry);
                    s = s.next;
                }
            }
            return nums;
};
```
