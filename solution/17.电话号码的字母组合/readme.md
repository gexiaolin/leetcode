# 17.电话号码的字母组合

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/letter-combinations-of-a-phone-number/)
+ 题目难度：medium

## 思路

由于不确定数字组合的长度，递归应该是第一个想到的解决方案。但是考虑到js递归的时间和空间消耗都比较大，本题尝试通过其他思路来解决问题。

我们可以逐一对每两个数字进行遍历得出这两个数字的组合结果，再用得到的结果和下一个数字进行遍历组合，依次进行至最后一个数字，即可得到最终的结果。

## 解答

```js
/**
 * @param {string} digits
 * @return {string[]}
 */
var letterCombinations = function(digits) {
    // 先声明每个数字对应的字母表
    const numMap = {
        '2': ['a', 'b', 'c'],
        '3': ['d', 'e', 'f'],
        '4': ['g', 'h', 'i'],
        '5': ['j', 'k', 'l'],
        '6': ['m', 'n', 'o'],
        '7': ['p', 'q', 'r', 's'],
        '8': ['t', 'u', 'v'],
        '9': ['w', 'x', 'y', 'z']
    };
    
    // 如果参数为空，直接返回空数组
    if (!digits) {
        return [];
    }

    // 把第一个数字对应的字母赋值给结果，并从第二个数字开始遍历
    let result = numMap[digits[0]];
    
    for (let i = 1; i < digits.length; i++) {
        // 我们需要一个中间数组做结果传递
        let mid = [];
        
        // 一个正常的时间复杂度为O(n*m)的组合遍历
        // 得到指定两个数字可以得到的所有组合
        // 把得到的这个值赋给结果变量，继续和下一个数字进行组合
        for (let j = 0; j < result.length; j++) {
            let nextArr = numMap[digits[i]];
            for (let k = 0; k < nextArr.length; k++) {
                mid.push(result[j] + nextArr[k]);
            }
        }
        
        result = mid;
    }
    
    return result;
};
```

## 性能

Runtime: 48 ms, faster than 96.45% of JavaScript online submissions for Letter Combinations of a Phone Number.

Memory Usage: 33.8 MB, less than 62.72% of JavaScript online submissions for Letter Combinations of a Phone Number.