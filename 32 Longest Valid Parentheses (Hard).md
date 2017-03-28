https://leetcode.com/problems/longest-valid-parentheses/#/description

32 Longest Valid Parentheses

> Given a string containing just the characters '(' and ')', find the length of the longest valid (well-formed) parentheses substring.
> 
> For "(()", the longest valid parentheses substring is "()", which has length = 2.
> 
> Another example is ")()())", where the longest valid parentheses substring is "()()", which has length = 4.

**分析**

栈中可以保存字符的下标，这样可以大大提高效率。

过程写在代码中。分情况讨论




**JAVA代码**

```
    public int longestValidParentheses(String s) {
        if (s ==null || s.length()==0) return 0;
        int start =-1;
        int maxLength =0;
        //建立一个栈用来存放下标
        Stack stack = new Stack();
        for (int i =0;i<s.length();i++) {
            if (s.charAt(i) == '(')
                stack.push(i);
            else {
                //如果此时为“)”,分情况讨论
                if (!stack.isEmpty()) {//栈非空
                    stack.pop();
                    //出栈后再分情况讨论：
                    if (stack.isEmpty())
                        maxLength = Math.max(maxLength, i - start);
                    else
                        maxLength = Math.max(maxLength, i - (int) stack.peek());
                } else //栈为空
                    start = i;
            }
        }
        return maxLength;
    }
```

