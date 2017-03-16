https://leetcode.com/problems/string-to-integer-atoi/?tab=Description

8  String to Integer (atoi)
> Implement atoi to convert a string to an integer.
> 
> Hint: Carefully consider all possible input cases. If you want a challenge, please do not see below and ask yourself what are the possible input cases.
> 
> Notes: It is intended for this problem to be specified vaguely (ie, no given input specs). You are responsible to gather all the input requirements up front.

**分析**

这个题的用意是要考察处理各种输入情况的能力，在将一个String转化为int时，需要考虑空格、空置、符号、非数字字符，还有是否溢出这些情况。

为了清晰的看到处理这些情况的过程，代码按步骤来写。

**JAVA实现**

```
/**
 * Created by hgx on 2017/3/10.
 */
 public static int myAtoi(String str) {
        int index = 0;//字符串索引
        int sign = 1; //符号
        int total = 0;//结果
        //空字符串
        if (str.length() == 0)
            return 0;
        //再去空格
        while (str.charAt(index) == ' ' && index < str.length())
            index++;
        //处理符号
        if (str.charAt(index) == '+' || str.charAt(index) == '-') {
            sign = (str.charAt(index) == '+') ? 1 : -1;
            index++;
        }
        //转换数字
        while (index < str.length()) {
            int digit = str.charAt(index) - '0';
            if (digit < 0 || digit > 9)
                break;
            //检查是否溢出
            if (Integer.MAX_VALUE / 10 < total || Integer.MAX_VALUE / 10 == total && Integer.MAX_VALUE % 10 < digit)
                return sign == 1 ? Integer.MAX_VALUE : Integer.MIN_VALUE;

            total = total * 10 + digit;
            index++;
        }
        return total * sign;
    }
```
