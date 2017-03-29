https://leetcode.com/problems/search-insert-position/#/description

35 Search Insert Position

> Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.
> 
> You may assume no duplicates in the array.
> 
> Here are few examples.

> [1,3,5,6], 5 → 2

> [1,3,5,6], 2 → 1

> [1,3,5,6], 7 → 4

> [1,3,5,6], 0 → 0



**分析**

这道题就采用典型的二分法来做就行。

有一点要提一下，如果二分法没找到target，结束后low的值正好停在比目标大的index上，high值一定停在恰好比目标小的index上。

**JAVA代码**

```
    public int searchInsert(int[] nums, int target){
        if (nums ==null ||nums.length==0) return 0;
        int low=0;
        int high = nums.length-1;
        while (low<=high){
            int mid = (low +high)/2;
            if (nums[mid] == target)
                return mid;
            else if (nums[mid]>target) high =mid-1;
            else low = mid+1;
        }
        return low;
    }
```
