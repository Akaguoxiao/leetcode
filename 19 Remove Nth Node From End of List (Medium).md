https://leetcode.com/problems/remove-nth-node-from-end-of-list/#/description

> Given a linked list, remove the nth node from the end of list and return its head.
> 
> For example,
> 
>    Given linked list: 1->2->3->4->5, and n = 2.
> 
>    After removing the second node from the end, the linked list becomes 1->2->3->5.

> Note:
> Given n will always be valid.
> Try to do this in one pass.

**题意**

删除链表中倒数第n个结点。

初步分析，设置两个指针left指向头结点，right=left+n-1.俩指针同时向后移动，直到j指针移动到最后一个元素，此时删除i指针的元素即可。但是写完代码发现，这样指针很难判断，容易报空指针异常错误。因为链表有可能只有一个节点。

所以修改代码，新增一个start指针指向head，让left和right指针同时指向start，然后让right先向后移动n个位置，然后再同时移动直到right到末尾。由于新增一个start指针，所以链表只有一个节点的元素也可以删除了。

**JAVA代码**


```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode start = new ListNode(0);
        ListNode left =start,right = start;
        start.next = head;
        for (int i =1;i<=n;i++){
            right = right.next;
        }
        //同时向后移动，直到right移动到链表的末尾
        while (right.next!= null){
            left = left.next;
            right= right.next;
        }
        //此时删除left的下一个节点即可
        left.next = left.next.next;
        return start.next;
    }
}
```
