# 26.删除排序数组中的重复项

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array/)
+ 题目难度：easy

## 思路

双指针，比较快慢指针的值，并返回慢指针。

## 解答

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var removeDuplicates = function(nums) {
    let i = 0;
    for (let j = 1; j < nums.length; j++) {
        if (nums[i] !== nums[j]) {
            i += 1;
            nums[i] = nums[j];
        }
    }
    
    return i + 1;
};
```

## 性能

Runtime: 56 ms, faster than 99.73% of JavaScript online submissions for Remove Duplicates from Sorted Array.

Memory Usage: 36.8 MB, less than 96.67% of JavaScript online submissions for Remove Duplicates from Sorted Array.