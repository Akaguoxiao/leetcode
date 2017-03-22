https://leetcode.com/problems/implement-strstr/#/description

28 Implement strStr()

> Implement strStr().
> 
> Returns the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

**题意**

这个题挂着一个Easy，让人觉得可以一句话解决。。。（其实本来就可以一句话解决return haystack.indexOf(needle);）不仅AC了，还超过了86%的玩家。

但是，我们得弄清楚背后的原理啊！

这道题就是让你判断，needle是不是haystack的子串，是的话就返回这个子串。

最基本的方法就是从Haystack的第一个位置开始逐个判断是不是子串。但是现在都流行KMP算法啊！

http://kb.cnblogs.com/page/176818/
http://blog.csdn.net/tkd03072010/article/details/6824326

这里就不赘述了，以上两篇博客解释的特别清楚。
