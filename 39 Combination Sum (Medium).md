https://leetcode.com/problems/combination-sum/#/description


39 Combination Sum (Medium)

> Given a set of candidate numbers (C) (without duplicates) and a target number (T), find all unique combinations in C where the candidate numbers sums to T.
> 
> The same repeated number may be chosen from C unlimited number of times.
> 
> Note:
> All numbers (including target) will be positive
> integers.
> 
> The solution set must not contain duplicate combinations.
> 
> For example, given candidate set [2, 3, 6, 7] and target 7, 
> 
> A solution set is: 
> 
> [
> 
>   [7],
>   
>   [2, 2, 3]
>   
> ]
> 


**分析**

给定一个数组，从中找出一组数来，使其和等于target。数组无序，但都是正整数。并且没有重复的数，但是一个数可以用多次。

要求返回无重复解且有序。

这样，我们可以采用深搜法来解决。先对数组进行排序，然后从小到大累加，等于或超过target时回溯。

为了避免重复遍历，我们搜索的时候只搜索当前或之后的数，而不再搜索前面的数。因为我们先将较小的数计算完，所以到较大的数时我们就不用再考虑有较小的数的情况了。

**JAVA代码**


```
    public List<List<Integer>> ansSet = new ArrayList<>();//全局变量存储答案集合


    public static List<List<Integer>> combinationSum(int[] candidates, int target){
        Arrays.sort(candidates);
        combinationSum(candidates,0,new ArrayList<Integer>(),target);
        return ansSet;
    }

    private  void combinationSum(int[] candidates, int begin, List<Integer> ans, int target){
        if (target==0){
            ansSet.add(ans);
            return;
        }
        for (int i =begin;i<candidates.length&&candidates[i]<=target;i++){
            List<Integer> cur = new ArrayList<>(ans);
            cur.add(candidates[i]);
            combinationSum(candidates,i,cur,target-candidates[i]);
        }
    }
```

