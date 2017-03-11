https://leetcode.com/problems/longest-common-prefix/?tab=Description

14 Longest Common Prefix

> Write a function to find the longest common prefix string amongst an array of strings.

**题意**

找出一个字符串数组中所有字符串的最长公共前缀。

**JAVA实现**


```
/**
 * Created by hgx on 2017/3/11.
 */
    public String longestCommonPrefix(String[] strs){
        if (strs ==null || strs.length==0)
            return "";
        String longestPrefix = strs[0];
        int i=1;
        while (i<strs.length){
            while(strs[i].indexOf(longestPrefix)!=0)
                longestPrefix =longestPrefix.substring(0,longestPrefix.length()-1);
            i++;
        }
        return longestPrefix;
    }
```
