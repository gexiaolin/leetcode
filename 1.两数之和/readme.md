# 1.两数之和

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/two-sum/submissions/)
+ 题目难度：easy
+ 数据结构：[哈希表](https://baike.baidu.com/item/%E5%93%88%E5%B8%8C%E8%A1%A8)

## 思路1

暴力法。简单有效，耗时较长。

## 解答1

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    for  (var i = 0; i < nums.length; i++) {
        for (var j = i + 1; j < nums.length; j++) {
            if (nums[i] + nums[j] === target) {
                return [i, j];
            }
        }
    }
};
```

## 性能1

执行用时 : 168 ms, 在Two Sum的JavaScript提交中击败了62.99% 的用户   
内存消耗 : 34.5 MB, 在Two Sum的JavaScript提交中击败了65.00% 的用户

## 思路2
js实现两遍[哈希表](https://baike.baidu.com/item/%E5%93%88%E5%B8%8C%E8%A1%A8)。

**重要！** es6的Map结构可以完美的实现哈希表，不了解的同学先移步[这里](http://es6.ruanyifeng.com/#docs/set-map#Map)做一下功课。

## 解答2

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    let myMap = new Map();
    // 第一遍哈希表，把所有的值-索引添加到表中
    for (let i = 0; i < nums.length; i++) {
        myMap.set(nums[i], i);
    }
    // 第二遍哈希表，从哈希表中查找是否有目标元素
    for (let i = 0; i < nums.length; i++) {
        let another = target - nums[i];
        if (myMap.has(another) && myMap.get(another) !== i) {
            return [i, myMap.get(another)];
        }
    }
};
```

## 性能2

执行用时 : 80 ms, 在Two Sum的JavaScript提交中击败了98.74% 的用户   
内存消耗 : 36 MB, 在Two Sum的JavaScript提交中击败了10.66% 的用户

## 思路3

js实现一遍[哈希表](https://baike.baidu.com/item/%E5%93%88%E5%B8%8C%E8%A1%A8)。我们可以不把全部的值-索引添加到表中，而是边检索边添加。

## 解答3

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    let myMap = new Map();
    for (let i = 0; i < nums.length; i++) {
        let another = target - nums[i];
        if (myMap.has(another) && myMap.get(another) !== i) {
            return [i, myMap.get(another)];
        }
        myMap.set(nums[i], i);
    }
    return [];
};
```

## 性能3
执行用时 : 104 ms, 在Two Sum的JavaScript提交中击败了81.69% 的用户   
内存消耗 : 35.1 MB, 在Two Sum的JavaScript提交中击败了24.28% 的用户
