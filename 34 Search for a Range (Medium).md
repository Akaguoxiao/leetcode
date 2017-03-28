https://leetcode.com/problems/search-for-a-range/#/description

34 Search for a Range

> Given an array of integers sorted in ascending order, find the starting and ending position of a given target value.
> 
> Your algorithm's runtime complexity must be in the order of O(log n).
> 
> If the target is not found in the array, return [-1, -1].
> 
> For example,

> Given [5, 7, 7, 8, 8, 10] and target value 8,

> return [3, 4].


**分析**

使用二分法找到target，然后分别向左向右找相等数字，最后返回下标。

**JAVA代码**


```
    public int[] searchRange(int[] nums,int target){
        int left=0;
        int right = nums.length-1;
        int[] res = {-1,-1};
        int start,end;
        int targetIndex = -1;
        while (left<= right){
            int mid = (right + left)/2;
            if (target == nums[mid]) {
                targetIndex = mid;
                break;
            }
            if (target<nums[mid]) right = mid-1;
            if (target>nums[mid]) left = mid+1;
        }
        if (targetIndex ==-1)
            return res;
        start=targetIndex;
        while (start>0 && nums[start-1] == nums[start]) start--;
        end =targetIndex;
        while (end<nums.length-1 &&nums[end+1] == nums[end]) end++;
        res[0]=start;
        res[1]=end;
        return res;
    }
    
```
