[Min Stack](https://leetcode.com/problems/min-stack/description/)

### 问题描述
Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

push(x) -- Push element x onto stack.
pop() -- Removes the element on top of the stack.
top() -- Get the top element.
getMin() -- Retrieve the minimum element in the stack.
Example:
```
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin();   --> Returns -3.
minStack.pop();
minStack.top();      --> Returns 0.
minStack.getMin();   --> Returns -2.
```

### 解法描述
1. 最小栈问题，使用JavaScript的Array类型中自带的push()与pop()方法即可实现

### 源码
```
/**
 * initialize your data structure here.
 */
var MinStack = function() {
        var stack = new Array(),
            minStack = new Array();

/** 
 * @param {number} x
 * @return {void}
 */
MinStack.prototype.push = function(x) {
        if (minStack.length === 0 || x <= minStack[minStack.length-1]){
            minStack.push(x);
        }
        stack.push(x);
};

/**
 * @return {void}
 */
MinStack.prototype.pop = function() {
        if (stack[stack.length-1] === minStack[minStack.length-1]){
            minStack.pop();
        }
        stack.pop();
};

/**
 * @return {number}
 */
MinStack.prototype.top = function() {
        return stack[stack.length-1];
};

/**
 * @return {number}
 */
MinStack.prototype.getMin = function() {
        return minStack[minStack.length-1];
};
    
};

/** 
 * Your MinStack object will be instantiated and called as such:
 * var obj = Object.create(MinStack).createNew()
 * obj.push(x)
 * obj.pop()
 * var param_3 = obj.top()
 * var param_4 = obj.getMin()
 */
```

### 运行时间

18 / 18 test cases passed.

Status: Accepted

Runtime: 88 ms

Your runtime beats 67.93 % of javascript submissions.
