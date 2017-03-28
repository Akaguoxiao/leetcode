https://leetcode.com/problems/search-in-rotated-sorted-array/#/description

> Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.
> 
> (i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).
> 
> You are given a target value to search. If found in the array return its index, otherwise return -1.
> 
> You may assume no duplicate exists in the array.

**分析**

平时我们二分法的时候，直接判断下中点和目标的关系，就可以知道目标在左半部分还是右半部份了，这背后其实隐含一个假设，那就是从起点到终点是一段有序的序列。

而本题中，如果我们还想继续做二分法，这个假设就不存在了，因为从起点到终点有可能有个断片！不过，旋转有序数组有一个特点，假设本身是个升序序列，从左向右。如果左边的点比右边的点小，说明这两个点之间是有序的，不存在旋转点。如果左边的点比右边的大，说明这两个点之间有一个旋转点，导致了不再有序。因为只有一个旋转点，所以一分为二后，肯定有一半是有序的。

所以，我们还是可以用二分法，不过要先判断左半边有序还是右半边有序。如果左半边有序，则直接将目标和左半边的边界比较，就知道目标在不在左半边了，如果不在左半边肯定在右半边。同理，如果右半边有序，则直接将目标和右半边的边界比较，就知道目标在不在右半边了，如果不在右半边肯定在左半边。这样就完成了二分。




**JAVA代码**


```
    public int search(int[] nums,int target){
        int left = 0;
        int right = nums.length-1;
        while (left<=right){
            int mid=(left + right)/2;
            if (nums[mid] == target)
                return mid;
            //如果左边一半为有序递增
            if (nums[left] <= nums[mid]){
                if (target< nums[mid] && target>=nums[left])
                    right = mid-1;
                else left = mid+1;
            }
            //如果右边一半为有序递增
            if (nums[mid]<= nums[right]) {
                if (target <= nums[right] && target > nums[mid])
                    left = mid + 1;
                else
                    right = mid-1;
            }
        }
        return -1;
    }
```
