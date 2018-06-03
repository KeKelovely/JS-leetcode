# 问题描述
There are 1000 buckets, one and only one of them contains poison, the rest are filled with water. They all look the same. If a pig drinks that poison it will die within 15 minutes. What is the minimum amount of pigs you need to figure out which bucket contains the poison within one hour.

Answer this question, and write an algorithm for the follow-up general case.

Follow-up:

If there are n buckets and a pig drinking poison will die within m minutes, how many pigs (x) you need to figure out the "poison" bucket within p minutes? There is exact one bucket with poison.

# 解法
1. 貌似是一个奥数题...假设有许多头（可怜的）猪，给你1个小时的时间，已知每只猪在痛饮一杯毒药后15min会阵亡，求最少需要多少只猪能找出1000杯水中的毒药？
2. 这里每只猪在不同的时间有5种结果，如：15死，30死，45死，60死，以及60活，分别对应毒药在第1,2,3,4,5杯中
3. 上面只是讨论了一维的情形，如果是二维呢？我们可以让1只猪在一小时内依次喝完每一行上的水，只要它没有撑死，那么，这只猪喝完该行后如果死掉，那么说明毒药必定在这一行上
4. 同理让另外1只猪在一小时内依次喝完每一列上的水，可以确定毒药所在的列。将行、列的结果合并，即可找出毒药的准确位置。
5. 实际上就是利用多维矩阵/向量来快速找出目标元素。三维的情况同理。
6. 放在一般情形下，1只猪最多可以处理n = (allTime / dieTime) + 1的情形，（如果猪最后活下来，说明没喝的那一行/列有毒，所以需要加1）,那么我们所求的就是以n为底的x桶水的对数

## 代码
```
/**
 * @param {number} buckets
 * @param {number} minutesToDie
 * @param {number} minutesToTest
 * @return {number}
 */
var poorPigs = function(buckets, minutesToDie, minutesToTest) {
    var count = parseInt(minutesToTest / minutesToDie) + 1;
    return Math.ceil(Math.log(buckets) / Math.log(count));
};
```
