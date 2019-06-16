# 13.罗马数字转整数

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/roman-to-integer/)
+ 题目难度：easy

## 思路

建立哈希表（无特殊key及顺序要求，本题简单用Object代替），如下：

```json
{
    "I": 1,
    "V": 5,
    "X": 10,
    "L": 50,
    "C": 100,
    "D": 500,
    "M": 1000
}
```

遍历给定字符串，比对当前字符对应的值及下一个字符对应的值，如果当前字符对应的值比较小，则用下一个字符的value减去当前字符的value。反之则直接在结果变量上加当前字符的value。

一次遍历，时间复杂度O(n)。

## 解答

```js
/**
 * @param {string} s
 * @return {number}
 */
var romanToInt = function(s) {
    const romanMap = {
        'I': 1,
        'V': 5,
        'X': 10,
        'L': 50,
        'C': 100,
        'D': 500,
        'M': 1000
    };
    let result = 0;

    for (let i = 0; i < s.length; i++) {
        // 如果当前字符value小于下一个字符value，需要做减处理，并把i++
        if (romanMap[s[i]] < romanMap[s[i + 1]] && i !== s.length - 1) {
            result += romanMap[s[i + 1]] - romanMap[s[i]];
            i += 1;
        } else {
            result += romanMap[s[i]];
        }
    }
    
    return result;
};
```

## 性能

Runtime: 132 ms, faster than 97.25% of JavaScript online submissions for Roman to Integer.

Memory Usage: 39.4 MB, less than 97.56% of JavaScript online submissions for Roman to Integer.
