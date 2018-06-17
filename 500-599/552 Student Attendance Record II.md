# 问题描述

[Click me](https://leetcode.com/problems/student-attendance-record-ii/description/)

# 解法描述
1. 本题将情况更加复杂化了，要求求出所有字符串可能排序结果中满足要求的个数，并需要整除一个10000007以避免溢出，所以可见结果是很大很复杂的
2. 这里需要用到动态规划DP的方法，简单来说，DP的思路就是要求的最优解一定是由子最优解推导出来的，常见于LCS（最长公共子序列）问题，用数学语言来说就是数组递推，如an一定可以由a1, a2, a3, ... an-1等推导得出
3. 这里因为我们要求所有满足要求的结果个数，由于结果非常复杂，应使用递推来做
4. 记所有以P结尾的字符串序列个数为Pn，用数组来存储，An、Ln同理
5. 然后分别找出Pn、An、Ln的递推式
6. Pn = Pn-1 + Ln-1 + An-1
7. Ln = An-1 + Pn-1 + An-2 + Pn-2(这里需要排除掉一种情况)
8. An = An-1 + An-2 + An-3，这里可以由题目要求所给的递推式推导得出
9. 最后递推求解n的情况即可。这里不妨将其看做一个多数列递推式的问题，也就是算法中的DP（动态规划）
10. 更详细的解法说明，可以参考[这里](https://www.cnblogs.com/grandyang/p/6866756.html)
# CODE
```
/**
 * @param {number} n
 * @return {number}
 */
var checkRecord = function(n) {
    var M = 1000000007,
        P = [], L = [], A = [];
        P[0] = 1, L[0] = 1, L[1] = 3,
        A[0] = 1, A[1] = 2, A[2] = 4;
    for (var i = 1; i < n; i++) {
        P[i] = ((P[i-1] + L[i-1]) % M + A[i-1]) % M;
        if ( i > 1 ) L[i] = ((A[i-1] + P[i-1]) % M + (A[i-2] + P[i-2]) % M) % M;
        if ( i > 2 ) A[i] = ((A[i-1] + A[i-2]) % M + A[i-3]) % M;
    }
    return ((A[n-1] + P[n-1]) % M + L[n-1]) % M;
};
```
