# 问题
[CLICK ME](https://leetcode.com/problems/judge-route-circle/description/)

# 解法
1. 很简单的题，要求判断机器人在按照字符串的顺序走完给定步数后是否会回到原位
2. 回到原来位置的条件就是n(U) = n(D) && n(L) = n(R)，嘛，暴力遍历一遍判断就行了，O(n)的复杂度
# 代码
```
/**
 * @param {string} moves
 * @return {boolean}
 */
var judgeCircle = function(moves) {
    var x = 0 // count for L & R
    var y = 0 // count for U & D
    for (var i = 0; i < moves.length; i++) {
        if (moves[i] == 'L') {
            x++
        }else if (moves[i] == 'R') {
            x--
        }else if (moves[i] == 'U') {
            y++
        }else if (moves[i] == 'D') {
            y--
        }
    }
    return (x == 0 && y == 0) ? true : false
};
```
