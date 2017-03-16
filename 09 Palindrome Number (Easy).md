https://leetcode.com/problems/palindrome-number/?tab=Description

9  Palindrome Number

> Determine whether an integer is a palindrome. Do this without extra space.

click to show spoilers.

Some hints:
> Could negative integers be palindromes? (ie, -1)
> 
> If you are thinking of converting the integer to string, note the restriction of using extra space.
> 
> You could also try reversing an integer. However, if you have solved the problem "Reverse Integer", you know that the reversed integer might overflow. How would you handle such case?
> 
> There is a more generic way of solving this problem.


**题意**

这道题需要判断一个整数是否是回文数。由于不能使用额外空间，所以不能用字符串来存储数字。经分析，从该数字的两头开始比较是否相等，然后去掉头尾两个数字继续比较，这是最简单的方法了。显而易见负数不是回文数。

**JAVA实现**


```
  public static boolean isPalindrome(int x){
        int head,tail;//数字的头尾
        if (x<0)
            return false;
        //首先计算x的位数
        int len=1;
        while (x/len>=10){
            len = len *10;
        }
        //比较x的头尾两个数字是否相等
        while (x!=0) {
            head = x / len;
            tail = x % 10;
            if (head != tail)
                return false;

            x = x % len / 10;
            len = len / 100;
        }
        return true;
        }
```
