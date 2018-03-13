# 21 Merge Two Sorted Lists
[Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/description/)
### 问题描述
Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

Example:

Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4
### 解法
1. 掌握JS中链表的表示与处理方法即可
2. 可以循环遍历两个Lists（条件：p1 && p2，即只要它们存在即可），也可以通过递归方法解决

### 源码实现
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
var mergeTwoLists = function(l1, l2) {
        if (l1 === null){
            return l2;
        }
        if (l2 === null){
            return l1;
        }
        if (l1.val <= l2.val){
            l1.next = mergeTwoLists(l1.next,l2);
            return l1;
        }
        if (l1.val > l2.val){
            l2.next = mergeTwoLists(l2.next,l1);
            return l2;
        }
};
```
### 运行时间

208 / 208 test cases passed.

Status: Accepted

Runtime: 72 ms

Your runtime beats 100.00 % of javascript submissions.
