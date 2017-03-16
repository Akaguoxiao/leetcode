https://leetcode.com/problems/3sum-closest/#/description

16 3Sum Closest

> Given an array S of n integers, find three integers in S such that the sum is closest to a given number, target. Return the sum of the three integers. You may assume that each input would have exactly one solution.

>     For example, given array S = {-1 2 1 -4}, and target = 1.
> 
>     The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).

**题意**

这道题在3Sum的基础上，改编成找最接近target的数字之和，但是这道题只有唯一解，所以不用担心重复问题。

在3Sum的算法上，新增一个min值，记录与target最近的res。

对于数组题，结果不要求返回位置相关信息的。最好都先考虑排序一下，然后再计算，会更简单直观，这个题也不例外。先排序一下：Arrays.sort(nums);


```
    public int threeSumClosest(int[] nums, int target) {
        Arrays.sort(nums);
        int result = nums[0] +nums[1]+nums[nums.length-1];
        for (int i = 0; i<nums.length-2;i++) {
            int low = i + 1, high = nums.length - 1;
            while (low < high) {
                int sum = nums[i] + nums[low] + nums[high]; 
                if (sum < target) low++;
                else high--;
                if (Math.abs(sum - target)<Math.abs(result- target))
                    result = sum;
            }
        }
        return result;
    }
```
