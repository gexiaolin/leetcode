# 24. 两两交换链表中的节点

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/swap-nodes-in-pairs/)
+ 题目难度：medium
+ 数据结构：[链表](https://baike.baidu.com/item/%E9%93%BE%E8%A1%A8)

## 思路

传统递归。以 `head + next` 为一组，并对下一组（ `next.next` 以及 `next.next.next`，第三与第四节点 ）的存在情况做判断，处理当前组的 `head` 和 `next` 指向，然后递归调用下一组的 `head + next` 。

需要考虑头节点不存在（空链表）的情况。

## 解答

```js
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var swapPairs = function(head) {
    if (!head || !head.next) return head;

    let next = head.next;
    let nextNext = next.next;

    if (next) {
        next.next = head;
        head.next = nextNext && nextNext.next || nextNext;

        if (nextNext) swapPairs(nextNext);
    }

    return next;
};
```

## 性能

执行用时 : 60 ms , 在所有 javascript 提交中击败了 91.22% 的用户

内存消耗 : 33.6 MB , 在所有 javascript 提交中击败了 50.00% 的用户

