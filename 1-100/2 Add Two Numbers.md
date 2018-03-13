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
