[Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/description/)
### 问题描述
Given a sorted linked list, delete all duplicates such that each element appear only once.

For example,
```
Given 1->1->2, return 1->2.
Given 1->1->2->3->3, return 1->2->3.
```

### 解法
1. 链表去重问题，也就是考察一下链表的基本操作。
2. 注意JavaScript中会存在**丢链**问题，因为JS是以Array的形式存储数组，每次只能放一个节点，所以每次输出只会有一个节点，所以要加一个prehead指针，指向
开始的头结点以防止丢链。

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
 * @return {ListNode}
 */
var deleteDuplicates = function(head) {
        var list = head,
            prehead = new ListNode();
        prehead.next = head;
        while (list !== null){
            if (list.next === null){
                break;
            }
            if (list.val === list.next.val){
                list.next = list.next.next;
            }else {
                list = list.next;
            }
        }
        return prehead.next;
};
```

### 时间


164 / 164 test cases passed.

Status: Accepted

Runtime: 76 ms

Your runtime beats 83.86 % of javascript submissions.
