# 14.最长公共前缀

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/longest-common-prefix/)
+ 题目难度：easy

## 思路

水平扫描，如果当前字母通过（所有元素都相同），加入结果变量。如果当前字母不通过（遇到某一个元素不相同），则直接返回现有结果，并停止扫描。

时间复杂度O(S)，S表示所有字母的数量。

## 解答

```js
/**
 * @param {string[]} strs
 * @return {string}
 */
var longestCommonPrefix = function(strs) {
    let result = '';
    
    if (!strs.length) {
        return result;
    }
    
    // 我们随便指定第一个元素做基准元素
    let baseLetter = strs[0];
    for (let i = 0; i < baseLetter.length; i++) {
        let currentLetter = baseLetter[i];
        for (let j = 0; j < strs.length; j++) {
            let compareLatter = strs[j][i];
            // 如果扫描不通过，直接返回结果，不继续扫描
            if (compareLatter !== currentLetter) {
                return result;
            } else if (compareLatter === currentLetter && j === strs.length - 1) {
                // 当扫描通过并且本次扫描已到最后一个元素，加入结果，进行下一轮扫描
                result += currentLetter;
            }
        }
    }
    
    return result;
};
```

## 性能

Runtime: 52 ms, faster than 96.76% of JavaScript online submissions for Longest Common Prefix.

Memory Usage: 34.9 MB, less than 63.45% of JavaScript online submissions for Longest Common Prefix.