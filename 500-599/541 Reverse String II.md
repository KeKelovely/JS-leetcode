# 问题描述

[Click me !](https://leetcode.com/problems/reverse-string-ii/description/)

# 解法描述

1. 依据题意分类讨论，假设数组中的元素个数为n，每次遍历2k个元素，这样只需翻转i - i+k个元素即可
2. 当数组中剩下的元素个数（即n-2mk, m为整数）小于2k时，两种情况，第一是剩余元素数大于或等于k，此时仍然翻转i - i+k个元素即可，第二种情况是剩余元素数不足k，此时翻转剩下的所有元素，即i - n
3. 注意上面的i、i+k和n指的都是下标每次遍历2k即可
4. JavaScript中只有Array自带有reverse方法，因此在转换到String上时需要做一些调整，比较简单，看代码就好了。

# Code

```
/**
 * @param {string} s
 * @param {number} k
 * @return {string}
 */
var reverseStr = function(s, k) {
    for (var i = 0; i < s.length; i = i + 2*k) {
        s = reverseOneString(s, i, Math.min(i+k, s.length));
    }
    return s;
};

var reverseOneString = function(s,start,end) {
    var tmp = s.substring(start, end).split("").reverse(),
        arr = s.split("");
    for (var i = start, j = 0; i < end; i++) {
        arr[i] = tmp[j++];
    }
    return arr.join("");
}
```
