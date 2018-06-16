# LeetCode By JavaScript
LeetCode Solutions (All By JavaScript!)
> [LeetCode](https://leetcode.com/)的个人Solutions汇总，全部使用JavaScript完成:satisfied:

> 目的：了解、掌握数据结构和算法，当然更重要的是学会如何用JS实现（如JS中的Hash Table、BST等），和JS结下更深的友谊:clap:

> 其他：做笔记备份的目的是方便以后复习和再学习，同时也看看以前写的算法是有多么傻x:shit:

## 基本格式
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

## Example
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
