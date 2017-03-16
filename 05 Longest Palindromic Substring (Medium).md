https://leetcode.com/problems/longest-palindromic-substring/?tab=Description


5  Longest Palindromic Substring


> Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.
> 
> Example:
> 
> Input: "babad"
> 
> Output: "bab"
> 
> Note: "aba" is also a valid answer.
> Example:
> 
> Input: "cbbd"
> 
> Output: "bb"


**题意**

找到最长的回文串，即从左右两边读都一样的字符串。
[http://www.cnblogs.com/bitzhuwei/p/Longest-Palindromic-Substring-Par-I.html](http://note.youdao.com/)

利用回文的中心对称特点，找出其回文即可。对于有N个字符的字符串S，有2N-1个中心（N个字符和N-1个空隙）。而围绕一个中心检测回文需要O(N)的时间，所以总时间复杂度是O(N^2)。



**JAVA算法**

```
    private int low,maxLen;//保存回文的起点索引和长度

    public String longestPalindrome(String s){
        int len = s.length();
        if (len <2)
            return s;
        for (int i=0;i<len-1;i++){
            extendPalindrome(s,i,i); //长度为奇数
            extendPalindrome(s,i,i+1);//长度为偶数
        }
        return s.substring(low,low+maxLen);
    }

    private void extendPalindrome(String s,int left ,int right){
        //以中心轴开始，向两边开始扫描字符
        while (left>= 0 && right <s.length() && s.charAt(left) ==s.charAt(right)){
            left--;
            right++;
        }
        if (maxLen <right-left-1){
            low = left +1;
            maxLen = right-left-1;
        }
    }
```
