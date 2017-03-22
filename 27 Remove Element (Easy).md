https://leetcode.com/problems/remove-element/#/description

27 Remove Element

> Given an array and a value, remove all instances of that value in place and return the new length.
> 
> Do not allocate extra space for another array, you must do this in place with constant memory.
> 
> The order of elements can be changed. It doesn't matter what you leave beyond the new length.
> 
> Example:
> Given input array nums = [3,2,2,3], val = 3
> 
> Your function should return length = 2, with the first two elements of nums being 2.

**题意**

这道题就挨个找呗，等于val那就删掉

**JAVA代码**


```

    public int removeElement(int[] nums, int val){
        if (nums ==null) return 0;
        int count=0;
        for (int i =0; i <nums.length;i++){
            if (nums[i] == val)
                continue;
            else
                nums[count++]=nums[i];
        }
        return count;
    }
```
