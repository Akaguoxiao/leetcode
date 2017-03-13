https://leetcode.com/problems/3sum/?tab=Description

15 3Sum
> Given an array S of n integers, are there elements a, b, c in S such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.

> For example, given array S = [-1, 0, 1, 2, -1, -4],
> 
> A solution set is:
> [
>   [-1, 0, 1],
>   [-1, -1, 2]
> ]

**题意**
求三个数的和为给定值。
先将数组排序，然后从第一个数字开始，令sum = 0-a[i]，然后再剩下的数组里从两端开始查找和为sum的组合；因为数组是递增的，所以如果剩下两数和大于sum，则high--，否则low++;

注意，在整个过程中要保证没有重复元素出现。很简单，在判断条件里加上如果a[i]!=a[i+1].

**JAVA**

```
    public List<List<Integer>> threeSum(int[] nums){
        //首先排序
        Arrays.sort(nums);
        List<List<Integer>> res = new ArrayList<>();
        for (int i =0;i<nums.length-2;i++) {
            if (i == 0 || (i > 0 && nums[i] != nums[i-1])) {
                int low = i + 1, high = nums.length - 1; //从剩下数组两端开始查找
                int sum = 0 - nums[i];  //剩下两数字相加为0-nums[i]
                while (low < high) {
                    if (nums[low] + nums[high] == sum) {
                        res.add(Arrays.asList(nums[i], nums[low], nums[high]));
                        //去重
                        while (low < high && nums[low] == nums[low + 1]) low++;
                        while (low < high && nums[high] == nums[high - 1]) high--;
                        //继续查找
                        low++;
                        high--;
                    } else if (nums[low] + nums[high] > sum) high--;
                    else low++;
                }
            }
        }
            return res;
    }
```
