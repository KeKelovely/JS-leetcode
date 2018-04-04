[Implement Stack using Queues](https://leetcode.com/problems/implement-stack-using-queues/description/)

### 问题描述
Implement the following operations of a stack using queues.

push(x) -- Push element x onto stack.
pop() -- Removes the element on top of the stack.
top() -- Get the top element.
empty() -- Return whether the stack is empty.
Notes:
You must use only standard operations of a queue -- which means only push to back, peek/pop from front, size, and is empty operations are valid.
Depending on your language, queue may not be supported natively. You may simulate a queue by using a list or deque (double-ended queue), as long as you use only standard operations of a queue.
You may assume that all operations are valid (for example, no pop or top operations will be called on an empty stack).

### 解法描述
1. 直接用JS的Array类型中的方法实现

### 源码
```
/**
 * Initialize your data structure here.
 */
var MyStack = function() {
    var stack = new Array();

/**
 * Push element x onto stack. 
 * @param {number} x
 * @return {void}
 */
MyStack.prototype.push = function(x) {
    	stack.push(x);
};

/**
 * Removes the element on top of the stack and returns that element.
 * @return {number}
 */
MyStack.prototype.pop = function() {
		var pop_element =  stack[stack.length-1];
    	stack.pop();
        return pop_element;
};

/**
 * Get the top element.
 * @return {number}
 */
MyStack.prototype.top = function() {
    	return stack[stack.length-1];
};

/**
 * Returns whether the stack is empty.
 * @return {boolean}
 */
MyStack.prototype.empty = function() {
        if (stack.length === 0){
            return true;
        }else{
            return false;
        }
};

};

/** 
 * Your MyStack object will be instantiated and called as such:
 * var obj = Object.create(MyStack).createNew()
 * obj.push(x)
 * var param_2 = obj.pop()
 * var param_3 = obj.top()
 * var param_4 = obj.empty()
 */
```
