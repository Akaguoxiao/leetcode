https://leetcode.com/problems/container-with-most-water/?tab=Description

11 Container With Most Water
> Given n non-negative integers a1, a2, ..., an, where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

Note: You may not slant the container and n is at least 2.

**题意**

找到条纵线然后这两条线以及X轴构成的容器能容纳最多的水。

开始时，我用双层循环计算任意两线段之间容量，但是这个O(n^2)的算法果断超时了。所以开始寻求简化算法：

假设我们最开始取两端的两条线段，这个时候宽度是max。以此为基准，为了增大容量，只能寻找高度更高的线段了。现在从左边开始，如果左边高于右边，那就将右边线段左移。这个时候又回到初始问题。

不断移动，直到左右指针相等为止。

**JAVA实现**


```
/**
 * Created by hgx on 2017/3/11.
 */
    public int maxArea(int[] height) {
        int volume;
        int maxVolume = 0;
        int left = 0,right = height.length-1;
        while (left<=right){
            volume = (right-left)*(Math.min(height[left],height[right]));
            maxVolume = Math.max(volume,maxVolume);
            if (height[left]<height[right])
                left++;
            else
                right--;
        }
        return maxVolume;
    }
```

