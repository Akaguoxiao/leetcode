https://leetcode.com/problems/4sum/#/description

18  4Sum

> Given an array S of n integers, are there elements a, b, c, and d in S such that a + b + c + d = target? Find all unique quadruplets in the array which gives the sum of target.
> 
> Note: The solution set must not contain duplicate quadruplets.
> 
> For example, given array S = [1, 0, -1, 0, -2, 2], and target = 0.
> 
> A solution set is:

> [

>   [-1,  0, 0, 1],

>   [-2, -1, 1, 2],

>   [-2,  0, 0, 2]

> ]

**题意**

这道题直接就可以利用之前的3Sum，无非就是再多套一层for循环即可。依然要注意去重

**JAVA**


```
   public List<List<Integer>> fourSum(int[] nums,int target){
        ArrayList<List<Integer>> res = new ArrayList<>();
        if (nums.length<4) return res;
        Arrays.sort(nums);
        for (int i = 0;i <nums.length-3;i++){
            //去重
            if (i>0 && nums[i]==nums[i-1]) continue;
            //接下来即是3Sum的算法了
            for (int j =i +1;j<nums.length-2;j++){
                if (j>i+1 && nums[j] == nums[j-1]) continue;
                int low = j+1,high = nums.length-1;
                while (low<high){
                    int sum = nums[i] +nums[j] +nums[low] + nums[high];
                    if (sum == target){
                        res.add(Arrays.asList(nums[i],nums[j],nums[low],nums[high]));
                        //去重
                        while (low<high && nums[low]==nums[low+1]) low++;
                        while (low<high && nums[high]==nums[high-1]) high--;
                        low++;
                        high--;
                    }else if (sum<target) low++;
                    else high--;
                }
            }
        }
        return res;
    }
```
