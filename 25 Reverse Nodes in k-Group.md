https://leetcode.com/problems/reverse-nodes-in-k-group/#/description

25 Reverse Nodes in k-Group

> Given a linked list, reverse the nodes of a linked list k at a time and return its modified list.

> k is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of k then left-out nodes in the end should remain as it is.
> 
> You may not alter the values in the nodes, only nodes itself may be changed.
> 
> Only constant memory is allowed.
> 
> For example,
> Given this linked list: 1->2->3->4->5
> 
> For k = 2, you should return: 2->1->4->3->5
> 
> For k = 3, you should return: 3->2->1->4->5

**题意**

这道题就是翻转链表的升级版，解决这道题就是循环翻转的过程，直到最后一个group的长度不足。

必须要掌握翻转链表的写法：
- 1. 首先设置一个前置节点，将前置节点的next设置为头节点，以头节点为当前节点，开始循环
- 2. 将当前节点的next赋给一个临时节点，然后将当前节点的next指向前置节点，随后依次位移前置节点指针和当前节点指针：前置节点指针指向当前节点，当前节点指针指向临时节点，这样就完成了一次循环
- 3. 当前置节点指针指向尾节点时，循环结束


有了这个翻转函数以后，只要对链表进行循环，当计数长度不为k时，指针继续前进；当计数长度到达k时，将头尾节点作为参数传入翻转函数进行翻转，然后重新拼接到原链表中，直至到达链表末尾。

**JAVA代码**


```
  public ListNode reverseKGroup(ListNode head,int k){
        if (head == null || head.next ==null || k==1)
            return head;

        ListNode first =head,last = head; //定义两个指针从头结点开始
        ListNode dummy = new ListNode(0); //dummy
        dummy.next =head;
        ListNode preGropu=dummy,nextGroup =dummy; //保存当前group的前一个指针和下一个group
        int count =1;
        //开始遍历链表，将k个链表作为一组翻转
        while (last!= null){
            if (count == k){
                nextGroup = last.next; //保存下一个group；
                reverseList(first,last); //将当前group进行翻转
                preGropu.next = last;  //当前group的前置指针指向last（翻转后last是第一个）
                preGropu = first;  //first反转后为最后一个，即下一个group的前置指针
                first.next = nextGroup; //把first指向下一个group
                first = nextGroup;
                last = nextGroup;
                count =1;//初始化计数器
                continue;//继续循环
            }

            last = last.next;
            count++;
        }
        return dummy.next;
    }

    private void reverseList(ListNode head,ListNode tail){
        ListNode pre = new ListNode(0); //新建一个指针指向前置节点
        ListNode cur = head;//新建一个指针指向当前节点
        pre.next = head;
        while (pre != tail){
            ListNode tmp = cur.next; //保存下一个节点
            cur.next = pre;  //反转，将当前节点指向前置节点
            pre = cur; //将pre后移
            cur = tmp;//将cur后移
        }
    }
```
