[Count Primes](https://leetcode.com/problems/count-primes/description/)

### 问题描述
Description:

Count the number of prime numbers less than a non-negative number, n.
### 解法描述
1. 找出比n小的数中的所有质数，暴力解法当然是一目了然，不过可以使用[Sieve of Eratosthenes](https://www.cnblogs.com/grandyang/p/4462810.html)算法将搜索范围缩小到sqrt(n)之内
2. 此外还需要写一个isPrime()函数，注意遍历范围到sqrt(n)即可

### 源码
```
/**
 * @param {number} n
 * @return {number}
 */
var countPrimes = function(n) {
    if (n <= 2){
        return 0;
    }
    var isprime = [],
        count = 0;
    for (var i = 0; i < n-1; i++){
        isprime.push(0);
    }
    for (var j = 2; j <= Math.sqrt(n); j++){
        if (isPrime(j) > 0){
            for (var k = j * j; k < n; k += j){
                isprime[k-1] = 1;
            }
        }
    }
    for (var m = 1; m < n; m++){
        if (isprime[m] === 0) count++;
    }
    return count;
};

var isPrime = function(num){
    for (var j = 2; j <= Math.sqrt(num); j++){
        if (num % j === 0){
            return -1;
        }
    }
    return 1;
}
```

### 运行时间


20 / 20 test cases passed.

Status: Accepted

Runtime: 180 ms

Your runtime beats 92.59 % of javascript submissions.
