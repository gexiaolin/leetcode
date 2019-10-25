# 53.最大子序和

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/maximum-subarray/)
+ 题目难度：easy

## 思路

使用动态规划进行逆向拆解，记录所有连续值 sum > 0 的情况，然后取出其中最大值。

一次遍历，时间复杂度O(n)。

## 解答

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var maxSubArray = function(nums) {
    let max = nums[0];
    let sum = 0;
    
    for (let i = 0; i < nums.length; i++) {
        sum += nums[i];
        max = Math.max(max, sum);
        sum = sum > 0 ? sum : 0;
    }
    
    return max;
};
```

## 性能

执行用时 : 64 ms, 在所有 javascript 提交中击败了 96.53% 的用户

内存消耗 : 35.1 MB, 在所有 javascript 提交中击败了 42.35% 的用户