https://leetcode.com/problems/wildcard-matching/#/description

44 Wildcard Matching (Hard)

> Implement wildcard pattern matching with support for '?' and '*'.


```
'?' Matches any single character.
'*' Matches any sequence of characters (including the empty sequence).

The matching should cover the entire input string (not partial).

The function prototype should be:
bool isMatch(const char *s, const char *p)

Some examples:
isMatch("aa","a") → false
isMatch("aa","aa") → true
isMatch("aaa","aa") → false
isMatch("aa", "*") → true
isMatch("aa", "a*") → true
isMatch("ab", "?*") → true
isMatch("aab", "c*a*b") → false
```


**分析**

这道题实现的其实就是正则匹配

过程写在代码注释里面

**JAVA**

```
    public static boolean isMatch(String s, String p){
        int i=0;
        int j=0;
        int mark = -1;//如果查询到*号，用来保存*下一个查询位置
        int begin = -1;//如果查询到*号，用来遍历字符串s直到找到查询字符串P中*的下一个字符

        while (i<s.length()){
            if (j<p.length() && (s.charAt(i) == p.charAt(j)||p.charAt(j)=='?')){
                i++;
                j++;
            }
            else if (j<p.length() && p.charAt(j)=='*'){
                mark = j++; //记录*的位置,并将j移动到下一位置
                begin=i;  //记录此时s的位置
            }
            //这里是关键，举例说明： s=abcd efgc cba x ba
            //为了方便看，添加了空格 p=abcd *    cba ? ba
            //注意看，这里s中efg后面接了2个c，本来*是代替efgc的，但是按照对比条件，ccba和cba是不符的
            //这个时候，就必须把efg后的c也当做*匹配。所以此时，j又回到*的下一个字符位置
            else if (mark!=-1) {//如果这个时候查询字符是*
                i=begin++; //继续遍历s
                j=mark+1; //j继续停留在*的下一位置。
            }else  return false;

        }
        while (j<p.length()&& p.charAt(j) == '*')
            j++;
        return j ==p.length();
    }

    public static void main(String[] args){
        Boolean ans = isMatch("abcdefgccbaxba","abcd*cba?ba");
        System.out.print(ans);
    }
```
