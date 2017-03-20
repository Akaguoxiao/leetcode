https://leetcode.com/problems/swap-nodes-in-pairs/#/description

24 Swap Nodes in Pairs

> Given a linked list, swap every two adjacent nodes and return its head.

> For example,
> Given 1->2->3->4, you should return the list as 2->1->4->3.
> 
> Your algorithm should use only constant space. You may not modify the values in the list, only nodes itself can be changed.

**题意**

题意很清楚，交换链表中相连两个结点。

Ps:涉及到修改表头的链表操作，可以用一个辅助指针dummy作为表头，这是链表中比较常用的小技巧，因为这样可以避免处理head的边界情况。

所以这道题就转换为：helper -> 1 -> 2 -> 3 -> 4

首先用pre指针保存每对的前一个结点，cur指针保存每对的第一个结点，再用一个nextstart指针保存下一对的第一个结点。这样就很方便了。

以第一对为开始，pre指向helper,cur指向1，nextstart指向3.首先将2的next指针指向1，再将helper的next指针指向2，再将1的指针指向3.完成后将pre指向2，cur指向3.开始下一轮。

**JAVA代码**


```
    public ListNode swapPairs(ListNode head){
        if (head == null)
            return null;
        ListNode dummy = new ListNode(0); //新增一个辅助指针作为表头，避免处理head的边界情况
        dummy.next = head;
        ListNode pre = dummy; //始终指向需要交换的Pair的前一个结点
        ListNode cur = head;  //始终指向需要交换的Pair的第一个结点
        while (cur!=null && cur.next!=null) {
            ListNode nextStart = cur.next.next; //指向下一个需要交换的pair的第一个结点，保证下一次交换
            cur.next.next = cur; //把第一个结点的next.next指向自己（即把第二个节点的next指向第一个结点）
            pre.next = cur.next;  //把第二个节点作为第一个节点
            cur.next = nextStart;
            pre = cur;
            cur = cur.next;
        }
        return dummy.next;
    }
```
