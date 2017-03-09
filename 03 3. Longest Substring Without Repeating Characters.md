https://leetcode.com/problems/longest-substring-without-repeating-characters/?tab=Description

3 Longest Substring Without Repeating Characters

> Given a string, find the length of the longest substring without repeating characters.
> 
> Examples:
> 
> Given "abcabcbb", the answer is "abc", which the length is 3.
> 
> Given "bbbbb", the answer is "b", with the length of 1.
> 
> Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
> 
> Subscribe to see which companies asked this question.


**题意**

给定一个字符串，找到最长子串（不重复），并返回其长度。

经分析，可以采用HashMap来存储每个字符(key,val),其中key存储字符，val存储其索引。用charAt函数可以很方便的根据索引返回值

定义两个指针i/j，i从字符串的第一个字符开始扫描，如果s.charAt(i)不在HashMap中，加入。否则，将j移到i的位置，同时记录此时找到的子串长度i-j+1.继续向后查找，找出最大的子串长度。



**JAVA实现**

```
/**
 * Created by hgx on 2017/3/9.
 */
    public static int lengthOfLongestSubstring(String s){
        if (s.length() ==0)return 0;
        //创建一个HashMap,key存储字符，val存储索引
        HashMap<Character , Integer> map = new HashMap<Character, Integer>();
        int max = 0;
        //定义i,j分别作为右左指针，i从左向右开始扫描
        for (int i=0,j=0;i<s.length();i++){
            if (map.containsKey(s.charAt(i))){
                //j要比较大小，因为这里HashMap中存的字符的位置可能在前面
                j =Math.max(j,map.get(s.charAt(i))+1);
            }
            map.put(s.charAt(i),i);
            max = Math.max(max,i-j+1);
        }
        return max;
    }
```
