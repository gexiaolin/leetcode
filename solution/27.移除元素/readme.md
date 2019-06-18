# 27.移除元素

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/remove-element/)
+ 题目难度：easy

## 思路

迭代匹配，通过splice方法进行元素移除。也可以使用双指针，通过快慢指针进行元素替换。

## 解答

```js
/**
 * @param {number[]} nums
 * @param {number} val
 * @return {number}
 */
var removeElement = function(nums, val) {
    let i = 0;
    for (i; i < nums.length; i++) {
        if (nums[i] === val) {
            nums.splice(i, 1);
            i--;
        }
    }
    return i + 1;
};
```

## 性能

Runtime: 52 ms, faster than 92.55% of JavaScript online submissions for Remove Element.

Memory Usage: 33.8 MB, less than 49.14% of JavaScript online submissions for Remove Element.