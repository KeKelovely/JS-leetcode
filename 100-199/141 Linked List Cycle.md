[Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/description/)

### 问题描述
Given a linked list, determine if it has a cycle in it.

Follow up:
Can you solve it without using extra space?

### 解法描述
1. 找出一个链表里是否有一个循环圈，当然可以建立一个哈希表，用以保存经过的节点，然后依次顺序循环，代价就是会付出O(n)的空间复杂度
2. 那么怎么考虑空间复杂度为O(1)的做法呢？也就是我们只能建立指针变量来遍历这个链表，但缺点是我们无法保存已经走过的路径，
换言之每次我们只能从指针上得到当前结点的情况，那么就可以利用快慢两个指针，只要这两个指针相遇，那么就说明存在循环圈。
3. O(1)的解法就是小学里面的相遇问题，如果存在cycle，那么跑得快的B一定会赶上跑得快的A。

### 代码实现
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
 * @return {boolean}
 */
var hasCycle = function(head) {
        if ( head === null || head.next === null){
            return false;
        }
        var p = head,
            sp = head;
        while ( sp !== null  && sp.next !== null){
            p = p.next;
            sp = sp.next.next;
            if ( p === sp){
                return true;
            }
        }
        return false;
};
```

### 运行时间
16 / 16 test cases passed.

Status: Accepted

Runtime: 64 ms

Your runtime beats 97.93 % of javascript submissions.
