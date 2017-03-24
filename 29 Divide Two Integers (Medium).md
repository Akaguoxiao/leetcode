https://leetcode.com/problems/divide-two-integers/#/description

29 Divide Two Integers

> Divide two integers without using multiplication, division and mod operator.
> 
> If it is overflow, return MAX_INT.

**题意**

不能用乘除法以及取模，所以只能用加减法来做了。

直接用除数去一个一个加，直到被除数被超过的话，会超时。

解决办法每次将被除数增加1倍，同时将count也增加一倍，如果超过了被除数，那么用被除数减去当前和再继续本操作。

**JAVA代码**


```
package com.example;

import com.sun.corba.se.spi.ior.IORFactories;

/**
 * Created by hgx on 2017/3/22.
 */

public class q_29_DivideTwoInteger {
    public int divide(int divedend, int divisor){
        //用long避免溢出
        int sign = 1;
        //判断相除符号
        if ((divedend > 0 && divisor <0) || (divedend <0 && divisor>0)){
            sign = -1;
        }
        long ldivedend = Math.abs((long)divedend);
        long ldivisor = Math.abs((long)divisor);
        //处理边界情况
        if (ldivisor == 0) return Integer.MAX_VALUE;
        if (ldivedend == 0 || ldivedend < ldivisor) return 0;
        long lres = ldivide(ldivedend,ldivisor);

        int res;
        if (lres > Integer.MAX_VALUE){
            res = (sign==1)?Integer.MAX_VALUE:Integer.MIN_VALUE;
        }else {
            res = (int)(sign*lres);
        }
        return res;

    }
    private long ldivide(long ldivedend , long ldivisor){
        if (ldivedend < ldivisor) return 0;
        //找到最大的乘数满足ldivisor * multiple<= ldivedend;
        //如果一项一项加肯定超时，所以就叠倍加，2,4,8,16,32.。。这样子就很快了
        long sum =ldivisor;
        long multiple = 1;
        while ((sum+ sum) <ldivedend){
            sum += sum;
            multiple += multiple;
        }

        return multiple + ldivide(ldivedend -sum ,ldivisor);
    }
}

```
