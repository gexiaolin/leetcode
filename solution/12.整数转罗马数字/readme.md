# 12.整数转罗马数字

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/integer-to-roman/)
+ 题目难度：medium

## 思路

把每一位的数字列表，遍历找出对应罗马字符。

## 解答

```js
/**
 * @param {number} num
 * @return {string}
 */
var intToRoman = function(num) {
    const romanTable = {
        3000: 'MMM',
        2000: 'MM',
        1000: 'M',
        900: 'CM',
        800: 'DCCC',
        700: 'DCC',
        600: 'DC',
        500: 'D',
        400: 'CD',
        300: 'CCC',
        200: 'CC',
        100: 'C',
        90: 'XC',
        80: 'LXXX',
        70: 'LXX',
        60: 'LX',
        50: 'L',
        40: 'XL',
        30: 'XXX',
        20: 'XX',
        10: 'X',
        9: 'IX',
        8: 'VIII',
        7: 'VII',
        6: 'VI',
        5: 'V',
        4: 'IV',
        3: 'III',
        2: 'II',
        1: 'I',
        0: ''
    };
    let result = '';
    let str = String(num);
    let len = str.length;
    for (let i = 0; i < len; i++) {
        result += romanTable[str[i] * (10 ** (len - i - 1))];
    }
    return result;
};
```

## 性能

Runtime: 136 ms, faster than 94.10% of JavaScript online submissions for Integer to Roman.

Memory Usage: 44.3 MB, less than 7.09% of JavaScript online submissions for Integer to Roman.