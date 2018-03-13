[Generate Parentheses](https://leetcode.com/problems/generate-parentheses/description/)

### 问题描述
Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

For example, given n = 3, a solution set is:
```
[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]
```
### 解法
1. 可以归结到一个搜索遍历问题中去。（或者说叫回溯法backtrack），开始基本操作：
- 初始条件：左右括号的数量n
- 约束条件：左右括号必须配对，但是这个条件太过于抽象，用数学语言来描述应该这样说：“字符串中的左括号数应不小于右括号数”
- 目标条件：找到所有满足约束条件，且括号数量均为n的配对字符串
2. 这样就可以写递归了：
- 初始条件：建立一个临时变量left,right用来表示**剩余的括号数**
- 约束条件：
① 若left > right，表示左括号数小于右括号数，此时什么都不做

② 若left > 0,放入一个左括号，并将left-1，用递归实现

③ 若right > 0 ,放入一个右括号，并将right-1，由于条件①的约束，这里只需要right>0就好了。

### 源码
```
/**
 * @param {number} n
 * @return {string[]}
 */
var DoParent = function(res,str,left,right){
            if (left === 0 && right === 0){
                res.push(str);
                return;
            }
            if (left > right) return;
            if (left > 0) DoParent(res,str + '(',left-1,right);
            if (right > 0)  DoParent(res,str + ')',left,right-1);
};
var generateParenthesis = function(n) {
            var res = [];
            DoParent(res,"",n,n);
            return res;
};
```
### 运行时间

8 / 8 test cases passed.

Status: Accepted

Runtime: 60 ms

Your runtime beats 100.00 % of javascript submissions.
