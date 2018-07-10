# 问题
[CLICK ME](https://leetcode.com/problems/dota2-senate/description/)
# 解法
1. 先大概翻译一哈题目：senate表示参议院（倒不如翻译成BP 233），在DOTA2中，分为天辉与夜魇两个阵营，某一天，当他们对争斗厌烦的时候，决定用互相BP（BAN PICK）
的方式来决定胜负，其中BP将按照给定的字符串从头到尾来进行，每当轮到某一名英雄时，它就可以Ban掉敌方阵营的一名英雄，使其丧失BP的资格，
当某一阵营的所有英雄全部丧失资格后，则判定另一方获胜
2. 本题可以抽象为一个字符串的顺序比较问题，既然涉及到顺序，那么用到的数据结构不是队列就是栈，其中队列对应JS中的unshift与shift方法，栈对应JS中的pop与push方法
3. 注意到本题要求从头到尾来BP，那么显然就用队列来实现，分别用q1,q2两个队列来存储两个阵营的BP顺序，每次取队列的第一个元素进行比较，位于前面（也就是序列小）的可以让对方出局，
换言之也就是让对方出队列，然后自己插入到队列的最后（因为是按一轮一轮的顺序来的，所以第一个BP后，会自动排到最后一个位置上）
4. 最后BP完，必然有一队为空，为空的这一队输掉游戏，另一方获胜
5. 思路和代码都比较简单，关键是理解本题应该使用队列问题，因为本题的关键在于顺序、比较，且是从前往后的顺序（如果是从后往前则用栈，即Pop与push方法）

# 代码
```
/**
 * @param {string} senate
 * @return {string}
 */
var predictPartyVictory = function(senate) {
    var q1 = [] // Radiant
    var q2 = [] // Dire
    var n = senate.length;
    for (var i = 0; i < n; i++) {
        senate[i] == 'R' ? (q1.push(i)) : (q2.push(i))
    }
    while (q1.length != 0 && q2.length != 0) {
        var a = q1[0]
        var b = q2[0]
        q1.shift()
        q2.shift()
        a < b ? (q1.push(a+n)) : (q2.push(b+n))
    }
    return q1.length > q2.length ? ('Radiant') : ('Dire')
};
```
