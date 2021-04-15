# LeetCode刷题记录

## 剑指offer

### 数组与矩阵

##### 3、数组中重复的数字

```java
找出数组中重复的数字。
在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

示例 1：
输入：
[2, 3, 1, 0, 2, 5, 3]
输出：2 或 3 
 
限制：
2 <= n <= 100000
```

题解1：

```java
空间复杂度n 时间复杂度n
class Solution {
    public int findRepeatNumber(int[] nums) {
        boolean[] flag=new boolean[nums.length];
        for(int i=0;i<nums.length;i++){
            if(flag[nums[i]]){
                return nums[i];
            }
            flag[nums[i]]=true;
        }
        return 0;
    }
}
```

题解2：使用set集合判断重复元素

题解3：

要求时间复杂度 O(N)，空间复杂度 O(1)。因此不能使用排序的方法，也不能使用额外的标记数组。

对于这种数组元素在 [0, n-1] 范围内的问题，可以将值为 i 的元素调整到第 i 个位置上进行求解。在调整过程中，如果第 i 位置上已经有一个值为 i 的元素，就可以知道 i 值重复。

以 (2, 3, 1, 0, 2, 5) 为例，遍历到位置 4 时，该位置上的数为 2，但是第 2 个位置上已经有一个 2 的值了，因此可以知道 2 重复：

```java
class Solution {
    public int findRepeatNumber(int[] nums) {
        for(int i=0;i<nums.length;i++){
            while(nums[i]!=i){
                if(nums[i]==nums[nums[i]])
                    return nums[i];
                int temp=nums[i];
                nums[i]=nums[temp];
                nums[temp]=temp;
            }
        }
        return 0;
    }
}
```

