[Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/description/)
### 问题描述
Remove all elements from a linked list of integers that have value val.

Example
Given: 1 --> 2 --> 6 --> 3 --> 4 --> 5 --> 6, val = 6
Return: 1 --> 2 --> 3 --> 4 --> 5

### 解法描述
1. 基本操作..JavaScript里面需要建立一个pre指针防止丢链

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
 * @param {ListNode} head
 * @param {number} val
 * @return {ListNode}
 */
var removeElements = function(head, val) {
    var pre = new ListNode(-1);
    pre.next = head;
    var p = pre;
    while (p.next !== null){
        if (p.next.val === val){
            p.next = p.next.next;
        }else{
            p = p.next;
        }
    }
    return pre.next;
};
```

### 运行时间

65 / 65 test cases passed.

Status: Accepted

Runtime: 80 ms

Your runtime beats 93.71 % of javascript submissions.
