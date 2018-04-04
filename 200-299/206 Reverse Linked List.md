[Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/description/)

### 问题描述
Reverse a singly linked list.

### 解法描述
1. 翻转一个单链表..就是把每个节点上指针的指向调转一个方向，基本操作，用一个空指针pre来实现（为什么是空指针？画图）
2. 最后return pre即可，因为pre就指向新的头结点，不用考虑JS中可能的丢链情形

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
 * @param {ListNode} head
 * @return {ListNode}
 */
var reverseList = function(head) {
    var pre = null,
        cur = head;
    while (cur !== null){
        var tmp = cur.next;
        cur.next = pre;
        pre = cur;
        cur = tmp;
    }
    return pre;
};
```
