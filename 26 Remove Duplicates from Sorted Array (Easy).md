https://leetcode.com/problems/remove-duplicates-from-sorted-array/#/description

> Given a sorted array, remove the duplicates in place such that each element appear only once and return the new length.
> 
> Do not allocate extra space for another array, you must do this in place with constant memory.
> 
> For example,
> Given input array nums = [1,1,2],
> 
> Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively. It doesn't matter what you leave beyond the new length.

**题意**

这道题就是删除数组中重复元素，简单的是该数组已经排好序了，所以连HashMap都不用，直接比较第i个和i-1个元素是否相等即可。

注意，此题不仅返回长度，还有修改后的数组！！！

**JAVA代码**


```
    public int removeDuplicates(int[] nums){
        int len = nums.length;
        if (nums ==null) return 0;
        if (len == 1) return 1;
        int count = 1;
        for (int i = 1 ;i<len; i++){
            if (nums[i] == nums[i-1]){
                continue;
            }
            else {
                nums[count] = nums[i];
                count++;
            }
        }
        return count;
    }
```
