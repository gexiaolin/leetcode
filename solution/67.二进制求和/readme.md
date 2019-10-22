# 67.二进制求和

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/add-binary/)
+ 题目难度：easy

## 思路

对短串补0，遍历求和。需要注意，如果第一位计算结束，借位尚有1，需要在结果第一位补1。

## 解答

```js
/**
 * @param {string} a
 * @param {string} b
 * @return {string}
 */
var addBinary = function(a, b) {
    let result = '';
    let aLen = a.length;
    let bLen = b.length;
    let spStr = '';

    // 计算需要给短串补多少个'0'
    for(let i = 0; i < Math.abs(aLen - bLen); i++) {
        spStr += '0';
    }
    // 短串补'0'
    aLen < bLen ? a = spStr + a : b = spStr + b;

    let borrow = 0;
    for (let i = a.length - 1; i >= 0; i--) {
        let sum = Number(a[i]) + Number(b[i]) + borrow;
        // 计算结果只有0 1 2 3这4种情况
        // 只有2和3需要把借位增为1
        if (sum === 2) {
            result = '0' + result;
            borrow = 1;
        } else if (sum === 3) {
            result = '1' + result;
            borrow = 1;
        } else {
            result = sum.toString() + result;
            borrow = 0;
        }
        
        // 如果便利结束，借位为1，需补至首位
        if (i === 0 && borrow === 1) result = '1' + result;
    }
    
    return result;
};
```

## 性能

执行用时 : 76 ms  在所有 javascript 提交中击败了 90.08% 的用户

内存消耗 : 35.5 MB , 在所有 javascript 提交中击败了 62.87% 的用户
