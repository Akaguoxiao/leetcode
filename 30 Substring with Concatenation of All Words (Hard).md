https://leetcode.com/problems/substring-with-concatenation-of-all-words/#/description

30 Substring with Concatenation of All Words (Hard)

> You are given a string, s, and a list of words, words, that are all of the same length. Find all starting indices of substring(s) in s that is a concatenation of each word in words exactly once and without any intervening characters.
> 
> For example, given:
> s: "barfoothefoobarman"
> words: ["foo", "bar"]
> 
> You should return the indices: [0,9].
> (order does not matter).

**题意**

乍一看Hard的题目挺难的，但是JAVA中有HashMap,那就方便多了。

首先将L中的单词都入map,由于L中单词不一定唯一，所以入map的时候得保存其出现个数。

然后从i=0开始遍历S，用subString将S截取为L中单词的长度的子串，比对是否为Map中的单词。这里要注意L中单词个数的问题，以及不能修改map，所以要创建Map的副本。

代码思想很简单，但是提交后运行效率不尽人意。测试用例跑完要186ms，只超过了18%的人。

**JAVA代码**


```
    public static List<Integer> findSubstring(String S,String[] L){
        List<Integer> res = new ArrayList<Integer>();
        if (S == null || L == null || L.length ==0) return res;
        int len = L[0].length(); //由于L中字符长度都一样，所以L[0]的长度就是大家的长度

        Map<String,Integer> map = new HashMap<String, Integer>();
        for (String w : L){
            map.put(w,map.containsKey(w)?map.get(w)+1:1);
        }

        //由于需要在S中找到L中所有字符串出现的位置，所以i只用找到这，剩下的长度不够就不用看了。
        for (int i =0;i<=S.length() - len*L.length;i++){
            Map<String,Integer> copy = new HashMap<String, Integer>(map);//拷贝一个副本，避免改掉了原本
            //开始比对
            for (int j =0;j<L.length;j++){
                String str = S.substring(i + j*len,i+j*len +len);
                if (copy.containsKey(str)) { //包含str
                    int count = copy.get(str);
                    if (count == 1) copy.remove(str); //如果map中该字符串只有一个就去掉
                    else copy.put(str, count - 1); //个数-1
                    if (copy.isEmpty()) { //匹配到
                        res.add(i);
                        break;
                    }
                }else break;
            }
        }
        return res;
        }
```
