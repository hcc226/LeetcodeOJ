### 题目描述
```
输入一个链表，输出该链表中倒数第k个节点。为了符合大多数人的习惯，本题从1开始计数，即链表的尾节点是倒数第1个节点。例如，一个链表有6个节点，从头节点开始，它们的值依次是1、2、3、4、5、6。这个链表的倒数第3个节点是值为4的节点。
示例：
给定一个链表: 1->2->3->4->5, 和 k = 2.
返回链表 4->5.
```
链接：https://leetcode-cn.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof

### 我的AC代码
```
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} k
 * @return {ListNode}
 */
/* var getKthFromEnd = function(head, k) {
    let count = 0;
    let temp = head;
    while(head) {
        head = head.next;
        count++;
    }
    let target = count - k;
    count = 0
    while(temp) {
        if (count === target) {
            return temp;
        }
        count ++;
        temp = temp.next;
    }
}; */

 var getKthFromEnd = function(head, k) {
     let slow = head;
     let fast = head;
     while(k--) {
         fast = fast.next;
     }
     while(fast) {
         fast = fast.next;
         slow = slow.next;
     }
     return slow;
 }
```

### 题解
方法一：先循环遍历一遍计算链表的长度len，然后再遍历一遍，找到正数len-k的位置，返回链表即可
方法二：快慢指针。首先快指针往前走k步，此时快慢指针的距离相差为k，那么之后快慢指针同时向后移动，当快指针指向链表末端时，慢指针恰好指向倒数第k个节点，返回即可。
