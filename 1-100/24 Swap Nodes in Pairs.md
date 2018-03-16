[Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/description/)
### 问题描述
Given a linked list, swap every two adjacent nodes and return its head.

```
For example,
Given 1->2->3->4, you should return the list as 2->1->4->3.
```

Your algorithm should use only constant space. You may not modify the values in the list, only nodes itself can be changed.

### 解法
1. 考查对链表的基本操作，此处用ptr1指向需要交换的结点对的前一个结点，ptr2指向需要交换的结点对的第一个结点，相应的用变量prehead和head来作为起始
2. 然后就是交换指针，文字描述说不清楚，画个图就很好理解了。画交换前后的指针连接图，找对应关系即可
3. 最后返回prehead.next，不要直接返回head，防止丢链。

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
var swapPairs = function(head) {
            if (head === null || head.next === null){
                return head;
            }
            var prehead = new ListNode(-1);
            prehead.next = head;
            
            var ptr1 = prehead,
                ptr2 = head;
            while ( ptr2 !== null && ptr2.next !== null){
                var nextstart = ptr2.next.next;
                ptr2.next.next = ptr2;
                ptr1.next = ptr2.next;
                ptr2.next = nextstart;
                ptr1 = ptr2;
                ptr2 = ptr2.next;
            }
            return prehead.next;
};

```
### 运行时间


55 / 55 test cases passed.

Status: Accepted

Runtime: 60 ms

Your runtime beats 83.85 % of javascript submissions.
