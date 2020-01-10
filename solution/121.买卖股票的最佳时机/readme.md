# 121. 买卖股票的最佳时机

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock/)
+ 题目难度：easy

## 思路

双指针一次遍历，记录低谷及峰值，比较存储收益。

时间复杂度O(n)

空间复杂度O(1)

## 解答

```js
/**
 * @param {number[]} prices
 * @return {number}
 */
var maxProfit = function(prices) {
    // 边界判断
    if (!prices.length) return 0;

    // 初始化最佳收益及低谷/峰值
    let result = 0;
    let low = high = prices[0];
    for (let i = 1; i < prices.length; i++) {
        let current = prices[i];
        if (current < low) {
            // 如果当前值低于已记录的低谷值，需要重置low和high的值
            // 因为题目要求卖出必须在买入后
            low = high = current;
        } else if (current > high) {
            // 如果当前值高于low，说明此处可以卖出
            // 计算收益，比较后存储
            // 近更新high值，因为此后可能会有更佳的卖出时机
            result = Math.max(result, current - low);
            high = current;
        }
    }

    return result;
};
```
## 性能

执行用时 : 68 ms , 在所有 JavaScript 提交中击败了 86.10% 的用户

内存消耗 : 35.4 MB , 在所有 JavaScript 提交中击败了 38.03% 的用户
