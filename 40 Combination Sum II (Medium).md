https://leetcode.com/problems/combination-sum-ii/#/description

40 Combination Sum II

> Given a collection of candidate numbers (C) and a target number (T), find all unique combinations in C where the candidate numbers sums to T.
> 
> Each number in C may only be used once in the combination.
> 
> Note:
> All numbers (including target) will be positive integers.
> The solution set must not contain duplicate combinations.
> For example, given candidate set [10, 1, 2, 7, 6, 1, 5] and target 8, 
> A solution set is: 


```
[
  [1, 7],
  [1, 2, 5],
  [2, 6],
  [1, 1, 6]
]
```

**分析**

这道题和上一道基本一样，只是题目限制条件改成了每个数只能用一次。

还是采取上一道题的方法，但是在判断条件里要对重复元素进行去除。



**JAVA代码**


```
    public List<List<Integer>> ansSet = new ArrayList<>();

    public List<List<Integer>> combinationSum2(int[] candidates,int target){
        Arrays.sort(candidates);
        combinationSum2(candidates,0,new ArrayList<Integer>(),target);
        return ansSet;
    }

    private void combinationSum2(int[] candidates, int begin, List<Integer> ans, int target) {
        if (target ==0)
            ansSet.add(ans);
        for (int i=begin;i<candidates.length && candidates[i]<=target;i++){
            if (i>begin && candidates[i]==candidates[i-1]) continue;
            List<Integer> cur = new ArrayList<>(ans);
            cur.add(candidates[i]);
            combinationSum2(candidates,i+1,cur,target-candidates[i]);
        }
    }
```


