https://leetcode.com/problems/multiply-strings/#/description

43 Multiply Strings (Medium)

> Given two non-negative integers num1 and num2 represented as strings, return the product of num1 and num2.
> 
> Note:
> 
> The length of both num1 and num2 is < 110.

> Both num1 and num2 contains only digits 0-9.

> Both num1 and num2 does not contain any leading zero.

> You must not use any built-in BigInteger library or convert the inputs to integer directly.

**分析**

这种大数的运算，使用高精度算法。

高精度算法，属于处理大数字的数学计算方法。在一般的科学计算中，会经常算到小数点后几百位或者更多，当然也可能是几千亿几百亿的大数字。一般这类数字我们统称为高精度数，高精度算法是用计算机对于超大数据的一种模拟加，减，乘，除，乘方，阶乘，开方等运算。对于非常庞大的数字无法在计算机中正常存储，于是，将这个数字拆开，拆成一位一位的，或者是四位四位的存储到一个数组中， 用一个数组去表示一个数字，这样这个数字就被称为是高精度数。高精度算法就是能处理高精度数各种运算的算法，但又因其特殊性，故从普通数的算法中分离，自成一家。

**JAVA代码**


```
    public String multiply(String num1,String num2){
        int carry=0;
        int tmp;
        int ans[] = new int[num1.length()+num2.length()];
        StringBuilder builder = new StringBuilder();
        //高精度算法，按位乘然后存入数组
        for (int i=num1.length()-1;i>=0;i--){
            for (int j = num2.length()-1;j>=0;j--){
                ans[i+j+1] += (num1.charAt(i)-'0')*(num2.charAt(j)-'0');
            }
        }
        for (int i=ans.length-1;i>=0;i--){
            tmp = (ans[i]+carry)%10;
            carry = (ans[i]+carry)/10;
            ans[i] =tmp;
        }
        for (int num:ans)
            builder.append(num);
        //删除首位0
        while (builder.length()>1 && builder.charAt(0)=='0'){
            builder.deleteCharAt(0);
        }
        return builder.toString();
    }
```
