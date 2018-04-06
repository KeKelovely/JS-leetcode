[Ugly Number II](https://leetcode.com/problems/ugly-number-ii/hints/)

### 问题描述
Write a program to find the n-th ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. For example, 1, 2, 3, 4, 5, 6, 8, 9, 10, 12 is the sequence of the first 10 ugly numbers.

Note that 1 is typically treated as an ugly number, and n does not exceed 1690.

### 解法描述
1. 与上一题相似，本题要求求出第n个ugly number，我觉得这题实质还是个奥数trick，所有的ugly number构成一个序列，每次取最小的那个作为uglynumber，题目中的Hints如下：
```
The naive approach is to call isUgly for every number until you reach the nth one. Most numbers are not ugly. Try to focus your effort on generating only the ugly ones.

An ugly number must be multiplied by either 2, 3, or 5 from a smaller ugly number.

The key is how to maintain the order of the ugly numbers. Try a similar approach of merging from three sorted lists: L1, L2, and L3.

Assume you have Uk, the kth ugly number. Then Uk+1 must be Min(L1 * 2, L2 * 3, L3 * 5).
```

### 源码描述
```
/**
 * @param {number} n
 * @return {number}
 */
var nthUglyNumber = function(n) {
	var res = [1];
	var i1 = 0,
		i2 = 0,
		i3 = 0;
	while (res.length < n){
		var m1 = res[i1] * 2, m2 = res[i2] * 3, m3 = res[i3] * 5,
			minnumber = Math.min(m1,m2,m3);
		if (m1 === minnumber) ++i1;
		if (m2 === minnumber) ++i2;
		if (m3 === minnumber) ++i3;
		res.push(minnumber);
	}
	return res[res.length-1];
};
```
