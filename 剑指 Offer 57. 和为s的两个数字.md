### 题目描述
```
输入一个递增排序的数组和一个数字s，在数组中查找两个数，使得它们的和正好是s。如果有多对数字的和等于s，则输出任意一对即可。

示例 1：

输入：nums = [2,7,11,15], target = 9
输出：[2,7] 或者 [7,2]
示例 2：

输入：nums = [10,26,30,31,47,60], target = 40
输出：[10,30] 或者 [30,10]
 

限制：

1 <= nums.length <= 10^5
1 <= nums[i] <= 10^6
```
链接：https://leetcode-cn.com/problems/he-wei-sde-liang-ge-shu-zi-lcof


### AC代码
```
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    for(let left = 0, right = nums.length - 1; left < right;) {
        const sum = nums[left] + nums[right];
        if (sum === target) {
            return [nums[left], nums[right]];
        }
        if (sum < target) {
            left++;
        }
        else {
            right--;
        }
    }
};
```

### 题目解析
本题重要的线索就是“数组是递增排序的数组”，那么我们从两边数字的和开始计算，如果和大于目标数字，那么就将右边索引往左移动，否则将左边索引往右移动，直到两数之和等于目标数字。
