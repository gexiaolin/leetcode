# 91. 解码方法

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/decode-ways/)
+ 题目难度：medium

## 思路

这道题思路和爬楼梯的思路一致，动态规划拆分最小解，一拍脑袋，3分钟就能想到状态转移方程：f(n) = f(n - 1) + f(n - 2)。但是这道题通过率非常低，因为非常容易漏掉一些边界情况。。

重新考虑边界情况后列出状态转移方程：

+ 当前数与前一个数可组合时：f(n) = f(n - 1) + f(n - 2)
+ 当前数与前一个数不可组合时：f(n) = f(n - 1)
+ 当前数为0时：f(n) = f(n - 2)

## 解答

```js
/**
 * @param {string} s
 * @return {number}
 */
var numDecodings = function(s) {
    if (s[0] === '0') return 0;

    const len = s.length;
    const result = [1];

    for (let i = 1; i < len; i ++) {
        let currentNum = parseInt(s[i]);
        let prevNum = parseInt(s[i - 1]);
        let sum = parseInt(s[i - 1] + s[i]);

        if (currentNum === 0 && (sum > 26 || prevNum === 0)) return 0;
        if (i === 1) {
            result[i] = currentNum === 0 || sum > 26 ? 1 : 2;
        } else if (currentNum === 0 || prevNum === 0) {
            result[i] = result[i - 2];
        } else if (sum > 26) {
            result[i] = result[i - 1];
        } else {
            result[i] = result[i - 1] + result[i - 2];
        }
    }

    return result[len - 1];
};
```

## 性能（待优化）

执行用时 : 72 ms , 在所有 JavaScript 提交中击败了 61.61% 的用户

内存消耗 : 36.2 MB , 在所有 JavaScript 提交中击败了 14.29% 的用户
