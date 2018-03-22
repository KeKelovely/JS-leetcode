[Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/)
### 问题描述
Say you have an array for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (ie, buy one and sell one share of the stock multiple times). However, you may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).
### 解法
1. 和上一题一样，只不过变成了你可以无限次的买入卖出，嘛，也就是说只要有的赚你就卖，然后再买再卖，然后基本操作
### 源码
```
/**
 * @param {number[]} prices
 * @return {number}
 */
var maxProfit = function(prices) {
            var max = 0;
            for (var i = 0; i < prices.length-1; i++){
                if (prices[i] < prices[i+1] ){
                    max += prices[i+1] - prices[i];
                }
            }
            return max;
};
```
### 时间

198 / 198 test cases passed.

Status: Accepted

Runtime: 64 ms

Your runtime beats 90.16 % of javascript submissions.
