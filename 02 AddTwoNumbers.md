https://leetcode.com/problems/add-two-numbers/?tab=Description

2. Add Two Numbers
> You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.
> 
> You may assume the two numbers do not contain any leading zero, except the number 0 itself.
> 
> Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
> Output: 7 -> 0 -> 8

**题意：**
让两个链表相加，得到另一个链表。
这道题要考虑这两个链表的长度是否相同，长度少的那个需要补0。


**JAVA实现：**
```
/**
 * Created by hgx on 2017/3/8.
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    public ListNode addTwoNumbers(ListNode l1,ListNode l2){
        ListNode prev = new ListNode(0);
        ListNode head = prev;
        int carry = 0;//存放进位
        while (l1 != null || l2 != null || carry != 0){
            int sum = 0;
            ListNode result = new ListNode(0);
            sum = ((l1 == null)? 0 : l1.val) + ((l2 ==null)?0 :l2.val) + carry;
            result.val =sum%10;
            carry = sum /10;
            prev.next = result;
            prev =result;

            l1 = (l1 ==null)? l1 : l1.next;
            l2 = (l2 ==null)? l2 : l2.next;
        }
        return head.next;
    }
}
```
