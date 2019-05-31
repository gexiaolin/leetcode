# 3.无重复字符的最长子串

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)
+ 题目难度：medium

## 思路
暴力法，取所有子串，筛选出最长的目标子串。这个大约会击败0%的人，用时1500ms左右，就不做分析了...

用滑动窗口的思路去解决这个问题，即：依次向后滑动（拼接）当前子串，每次拼接时检测即将拼接的字符是否出现在当前的子串中，如果出现过，记录并比较目前为止的最长子串，然后删除当前子串开始位置至出现位置的所有字符。

这样索引j将会迭代n次，时间复杂度O(n)。

## 解答

```js
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
    let len = 0;
    let str = '';
    
    for (let i = 0; i < s.length; i++) {
        if (str.indexOf(s[i]) !== -1) {
            str = str.slice(str.indexOf(s[i]) + 1);
        }
        str += s[i];
        len = Math.max(str.length, len);
    }
    return len;
};
```

## 性能

执行用时 : 112 ms, 在Longest Substring Without Repeating Characters的JavaScript提交中击败了98.16% 的用户

内存消耗 : 40.3 MB, 在Longest Substring Without Repeating Characters的JavaScript提交中击败了48.95% 的用户
