https://leetcode.com/problems/two-sum/?tab=Description

**1. Two Sum**

> Given an array of integers, return indices of the two numbers such that they add up to a specific target.
> 
> You may assume that each input would have exactly one solution, and you may not use the same element twice.
> 
> Example:
> Given nums = [2, 7, 11, 15], target = 9,
> 
> Because nums[0] + nums[1] = 2 + 7 = 9,
> return [0, 1].



**题意：**

给定一个数组和一个target,这个数组中恰有两个数字相加等于target。求这两个数字的位置index;




**JAVA实现：**

```
/**
 * Created by hgx on 2017/3/3.
 */

public class q_01_TwoSum {
 
    public  static int[] twoSum(int[] nums,int target){
        int[] result = new int[2];
        Map<Integer ,Integer> map = new HashMap<Integer, Integer>();
        for(int i=0;i<nums.length;i++){
            if (map.containsKey(target - nums[i])){
                result[0] = map.get(target-nums[i]);
                result[1] = i;
                return result;
            }
            map.put(nums[i],i);
        }

        return result;
    }
}

```
