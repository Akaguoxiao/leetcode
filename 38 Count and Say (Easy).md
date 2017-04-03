https://leetcode.com/problems/count-and-say/#/description

38 Count and Say

> The count-and-say sequence is the sequence of integers beginning as follows:

> 1, 11, 21, 1211, 111221, ...
> 
> 1 is read off as "one 1" or 11.

> 11 is read off as "two 1s" or 21.

> 21 is read off as "one 2, then one 1" or 1211.

> Given an integer n, generate the nth sequence.

> 
> Note: The sequence of integers will be represented as a string.



**分析**

第一种情况：n<0时返回null。 

第二种情况：当n=1时，返回1 

第三种情况：当n>1时，假设n-1返回的字符串是s，对s的串进行处理理，对不同的数字进行分组比如112365477899，分成11，2，3，6，5，4，77，8，99。最有就2个1，1个2，1个3，1个6，1个5，一个4，2个7，1个8，2个9，就是211213161614271829，返回此结果。 

　　
**JAVA代码**


```
package com.example;

import java.util.HashMap;

/**
 * Created by hgx on 2017/4/3.
 */

public class q_38_CountAndSay {
    public String countAndSay(int n){
        if (n<1)
            return null;
        String res="1";
        for (int i=2;i<=n;i++){
            res = solve(res);
        }
        return res;
    }

    private static String solve(String str){
        StringBuilder builder = new StringBuilder();
        int count =1;
        for (int i=1;i<str.length();i++){
            //把不同的数字分组，相同的一组然后计数
            if (str.charAt(i) ==str.charAt(i-1)){
                count++;
            }
            else {
                builder.append(count).append(str.charAt(i-1));
                count=1;
            }
        }
        //处理最后一个字符
        builder.append(count).append(str.charAt(str.length()-1));
        return builder.toString();
    }


}

```
