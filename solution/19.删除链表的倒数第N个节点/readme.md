# 19.删除链表的倒数第N个节点

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/)
+ 题目难度：medium
+ 数据结构：[链表](https://baike.baidu.com/item/%E9%93%BE%E8%A1%A8)

## 思路

最简单的思路是第一次遍历拿到链表的长度，第二次遍历处理倒数第n + 1个节点的next指向。

我们直接处理进阶问题：使用一次遍历完成题目要求。使用双指针，第二个指针正常遍历，第一个指针当第二个指针距离它n步以后再跟随一起进行next指向前进。当指针二的next为null时，处理指针一的next指向即可达成题目要求。

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
 * @param {number} n
 * @return {ListNode}
 */
var removeNthFromEnd = function(head, n) {
    // 声明双指针，声明一个计数器来计算两个指针之间的距离
    let cur1 = head;
    let cur2 = head;
    let count = 0;

    while (cur2.next) {
        // 当计数器大于等于n的时候，指针一开始移动
        if (count >= n) {
            cur1 = cur1.next;
        }
        
        cur2 = cur2.next;
        count += 1;
    }
    
    // 判断两种边界情况，一种是删除的节点为第一个节点，另一种是删除的节点为最后一个节点
    if (count === n - 1) {
        return head.next;
    } else {
        cur1.next = n === 1 ? null : cur1.next.next;
    }
    
    return head;
};
```

## 性能

Runtime: 60 ms, faster than 83.81% of JavaScript online submissions for Remove Nth Node From End of List.

Memory Usage: 34 MB, less than 91.08% of JavaScript online submissions for Remove Nth Node From End of List.