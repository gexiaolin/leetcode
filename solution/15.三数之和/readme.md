# 15.三数之和

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/3sum/)
+ 题目难度：medium

## 思路

一道经典的算法面试题。

第一反应应该是对数组排序，这样方便去重以及确定指针移动方式。

然后可以把`a + b + c = 0`转化为`-a = b + c`，然后在确定a的前提下，来寻找b和c，这样就把题目转换成了一道可以用`双指针`解决的题目。

同时由于有一个长度非常大的测试用例，还需要通过剪枝优化来避免出现超时的情况（是的我踩坑了）。

## 解答

```js
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var threeSum = function(nums) {
    if (!nums.length || nums.length < 3) return [];
    
    // 数组从小到大排序
    nums = nums.sort((a, b) => a - b);
    
    let len = nums.length;
    let result = [];

    // 确定最小数字
    for (let i = 0; i < len; i++) {
        // 如果最小数字大于0，那么肯定不会出现符合规则的答案，直接break
        if (nums[i] > 0) break;

        // 如果最小数字重复，直接continue下一个数字
        if (i > 0 && nums[i] === nums[i - 1]) continue;

        let l = i + 1;
        let r = len - 1;
        
        while (l < r) {
            // 接下来就比较简单了，因为数组经过排序，所以可以通过条件判断双指针的向中心移动
            if (r < len - 1 && nums[r] === nums[r + 1] || nums[i] + nums[l] + nums[r] > 0) {
                r--;
            } else if (l > i + 1 && nums[l] === nums[l-1] || nums[i] + nums[l] + nums[r] < 0) {
                l++;
            } else {
                result.push([nums[i], nums[l], nums[r]]);
                r--;
                l++;
            }
        }
    }

    return result;
};
```

## 性能

执行用时 : 200 ms , 在所有 JavaScript 提交中击败了 98.69% 的用户
内存消耗 : 47.4 MB , 在所有 JavaScript 提交中击败了 35.62% 的用户
