# 5.最长回文子串

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/longest-palindromic-substring/)
+ 题目难度：medium

## 思路

中心扩展，要考虑'bb'这种的字符串，中心应该在两个字母之间，而'aba'中心在字母'a'。遍历所有可能的中心点，存储该中心点左右扩展的最长回文串。

时间复杂度O(n^2)，空间复杂度O(l)。

## 解答

```js
/**
 * @param {string} s
 * @return {string}
 */
var longestPalindrome = function(s) {
    if (!s.length) return '';

    let start = 0;
    let end = 0;
    let len = (s.length - 1) * 2 - 1;

    const testCenter = (l, r) => {
        while (s[l] === s[r] && l >= 0 && r <= s.length) {
            if (r - l > end - start) {
                start = l;
                end = r;
            }

            r += 1;
            l -= 1;
        }
    };

    for (let i = 0; i < len; i++) {
        let l, r;
        if (i % 2 === 0) {
            l = i / 2;
            r = l + 1;
        } else {
            l = (i - 1) / 2;
            r = l + 2;
        }
        testCenter(l, r);
    }

    return s.slice(start, end + 1);
};
```

## 性能

执行用时 : 184 ms , 在所有 JavaScript 提交中击败了 63.50% 的用户
内存消耗 : 35.5 MB , 在所有 JavaScript 提交中击败了 85.09% 的用户
