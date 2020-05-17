### 题目描述
找出数组中重复的数字。

在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

示例 1：

输入：
[2, 3, 1, 0, 2, 5, 3]
输出：2 或 3 

限制：

2 <= n <= 100000
链接：https://leetcode-cn.com/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof

### 我的AC代码
```
/**
 * @param {number[]} nums
 * @return {number}
 */
 // 方法一：hash
/* var findRepeatNumber = function(nums) {
    let obj = {};
    let len = nums.length;
    for(let i = 0; i < len; i++) {
        if (obj[nums[i]]) {
            return nums[i];
        }
        else {
            obj[nums[i]] = 1;
        }
    }
}; */

// 方法二：排序交换
var findRepeatNumber = function(nums) {
    let len = nums.length;
    for(let i = 0; i < len; i++) {
        let num = nums[i];
        if (num === i) {
            continue;
        }
        else {
            if (num === nums[num]) {
                return num;
            }
            else {
                nums[i] = nums[num];
                nums[num] = num;
                i--;
            }
        }
    }
}
```
### 解题思路
方法一： 遍历数组，遇见一个数字使用hash存储下来，直到遇见已经存在于hash中的数字
方法二： 排序后再遍历，判断是否重复。
方法三： 仔细阅读本题可以发现，本题的特殊之处在于“在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内”，那么假如没有重复的数字，那么
数组下标为i的位置上数字为i。假如有重复的数字，那么有些数字可能位于多个位置，有些数字会不存在于数组中。
那么我们可以遍历这个数组，判断当前位置i的数字m，假如i===m那么继续判断下个位置，否则判断位置为m的数字n，假如m===n，那么证明这个数字重复，直接返回即可，
如果不相等的话，那么交换m和n的位置，继续判断，直到遇到重复的数字为止。
