# 70. 爬楼梯

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/climbing-stairs/)
+ 题目难度：sasy

## 思路

动态规划，拆解第n阶的解。第n阶可以从 `n - 1` 阶和 `n - 2` 阶上去，然后可以通过记录 `n - 1` 阶和第 `n - 2` 阶的解相加返回。

> 注意边界判断，0阶直接返回0，第1阶和第2阶拿不到 `n - 1` 或 `n - 2` 的值，需要单独处理。

## 解答

```js
/**
 * @param {number} n
 * @return {number}
 */
var climbStairs = function(n) {
    if (!n) return 0;

    if (n === 1 || n === 2) return n;

    let arr = [1, 2];
    for (let i = 3; i <= n; i++) {
        arr.push(arr[i - 1 - 1] + arr[i - 2 - 1]);
    }

    return arr[arr.length - 1];
};
```

## 性能

执行用时 : 48 ms , 在所有 javascript 提交中击败了 99.48% 的用户

内存消耗 : 33.8 MB , 在所有 javascript 提交中击败了 17.91% 的用户