# 问题

[Click me!](https://leetcode.com/problems/perfect-number/description/)

# 解法

1. 从2开始遍历到该数的平方根，找出每一个可以被整除的数即为所求的因子，然后累加求和
2. 最后注意排除掉1的情形，1不是完全数

# Code
```
/**
 * @param {number} num
 * @return {boolean}
 */
var checkPerfectNumber = function(num) {
	if (num == 1) return false;
    var sum = 1;
	for (var i = 2; i <= parseInt(Math.sqrt(num)); i++){
		if (num % i == 0){
			sum += i + (i * i == num? 0 : num / i);
		}
	}
	return sum == num;
};
```
