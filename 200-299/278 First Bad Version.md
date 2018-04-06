[First Bad Version](https://leetcode.com/problems/first-bad-version/description/)

### 问题描述
You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of your product fails the quality check. Since each version is developed based on the previous version, all the versions after a bad version are also bad.

Suppose you have n versions [1, 2, ..., n] and you want to find out the first bad one, which causes all the following ones to be bad.

You are given an API bool isBadVersion(version) which will return whether version is bad. Implement a function to find the first bad version. You should minimize the number of calls to the API.

### 解法描述
1. 仔细阅读题干，发现本题实质是在考查二分查找，然后正常操作完成之

### 源码描述
```
/**
 * Definition for isBadVersion()
 * 
 * @param {integer} version number
 * @return {boolean} whether the version is bad
 * isBadVersion = function(version) {
 *     ...
 * };
 */

/**
 * @param {function} isBadVersion()
 * @return {function}
 */
var solution = function(isBadVersion) {
    /**
     * @param {integer} n Total versions
     * @return {integer} The first bad version
     */
    return function(n) {
        var left = 1, right = n;
        while (left < right){
            var mid = parseInt((left + right) / 2);
            if (!isBadVersion(mid))   left =  mid + 1;
            else right = mid;
        }
        return left;
    };
};
```
