[Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/description/)

### 问题描述
Write a program to find the node at which the intersection of two singly linked lists begins.


For example, the following two linked lists:
```
A:          a1 → a2
                   ↘
                     c1 → c2 → c3
                   ↗            
B:     b1 → b2 → b3
begin to intersect at node c1.
```

Notes:

If the two linked lists have no intersection at all, return null.
The linked lists must retain their original structure after the function returns.
You may assume there are no cycles anywhere in the entire linked structure.
Your code should preferably run in O(n) time and use only O(1) memory.
### 解法描述
1. 找到两个链表相交的地方，和之前那到在链表里找cycle的题类似，空间复杂度为O(1)的解法同样使用两个指针来实现
2. 两个指针速度相同，只要让它们跑过相同的节点数，相遇的地方一定就是两个链表的交点
3. 这里为了让它们跑过的节点数相同，就让a节点在遍历完a链表后，从headB开始遍历b链表，b节点同理从headA开始遍历a链表，相遇时它们都会经过a+b的步长
4. 相遇的地方（a===b）也就是两个链表的“Intersection”

### 源码
```
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */

/**
 * @param {ListNode} headA
 * @param {ListNode} headB
 * @return {ListNode}
 */
var getIntersectionNode = function(headA, headB) {
            if (headA === null || headB === null){
                return null;
            }
            var a = headA,
                b = headB;
            while (a !== b){
                a = (a === null ? headB : a.next);
                b = (b === null ? headA : b.next);
            }
            return a;
};
```
### 运行时间


42 / 42 test cases passed.

Status: Accepted

Runtime: 92 ms

Your runtime beats 95.07 % of javascript submissions.
