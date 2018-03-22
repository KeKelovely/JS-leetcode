[Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)

### 问题描述

Say you have an array for which the ith element is the price of a given stock on day i.

If you were only permitted to complete at most one transaction (ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.

**Example 1:**
```
Input: [7, 1, 5, 3, 6, 4]
Output: 5
```

max. difference = 6-1 = 5 (not 7-1 = 6, as selling price needs to be larger than buying price)
**Example 2:**
```
Input: [7, 6, 4, 3, 1]
Output: 0
```
In this case, no transaction is done, i.e. max profit = 0.

### 解法
1. 最简单的做法就是暴力递归套个双重循环，当然我们有更加优雅的处理方法可以选择
2. 试着将这个问题抽象成数学表达式就是：
```
对i,j∈[0,prices.length-1],且i<j,求max(pirces[j] - prices[i])
```
3. 由于i,j相互独立，因此可以间接转化为求max_pirces[j]和min_prices[i],只不过多了一个约束条件i<j
4. 剩下就是基本操作，以pirces[0]作为起始min值，起始max值为0，然后依次遍历整个数组，遇到最小值就赋值，遇到最大值就赋值

### 源码
```
/**
 * @param {number[]} prices
 * @return {number}
 */
var maxProfit = function(prices) {
        var max = 0,
            min = prices[0];
        for (var i = 1; i < prices.length; i++){
            if (prices[i] < min){
                min = prices[i];
            }
            else if (prices[i] - min > max){
                max = prices[i] - min;
            }
        }
        return max;
};
```
### 时间

200 / 200 test cases passed.

Status: Accepted

Runtime: 64 ms

Your runtime beats 94.01 % of javascript submissions
