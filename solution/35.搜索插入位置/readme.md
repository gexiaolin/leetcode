# 35.搜索插入位置

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/search-insert-position/)
+ 题目难度：easy

## 思路

正常遍历数组可在O(l)时间复杂度下解决这个问题。更简便的方法是二分查找，可快速解决。

## 解答

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var searchInsert = function(nums, target) {
    let l = 0;
    let r = nums.length - 1;
    
    // 边界判断
    if (nums[l] > target) return 0;
    if (nums[r] < target) return r + 1;

    let m = Math.floor((r + l) / 2);
    let result;
    
    // 二分查找，通过中间值与目标值的比较缩减二分范围
    while (!result && result !== 0) {
        if (nums[m] === target) {
            result = m;
        } else if (nums[l] === target) {
            result = l;
        } else if (nums[r] === target || l + 1 === r) {
            result = r;
        } else {
            if (nums[m] < target) l = m;
            if (nums[m] > target) r = m;
            m = Math.floor((r + l) / 2);
        }
    }
    
    return result;
};
```

## 性能

执行用时 : 64 ms , 在所有 JavaScript 提交中击败了 98.19% 的用户
内存消耗 : 34.3 MB , 在所有 JavaScript 提交中击败了 32.70% 的用户
