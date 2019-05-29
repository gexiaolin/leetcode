# 1.两数之和

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/two-sum/submissions/)
+ 题目难度：easy

## 思路

暴力法。

## 解答

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    for  (var i = 0; i < nums.length; i++) {
        for (var j = i + 1; j < nums.length; j++) {
            if (nums[i] + nums[j] === target) {
                return [i, j];
            }
        }
    }
};
```

## 性能

执行用时 : 168 ms, 在Two Sum的JavaScript提交中击败了62.99% 的用户   
内存消耗 : 34.5 MB, 在Two Sum的JavaScript提交中击败了65.00% 的用户
