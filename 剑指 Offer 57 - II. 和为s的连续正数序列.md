### 题目描述
```
输入一个正整数 target ，输出所有和为 target 的连续正整数序列（至少含有两个数）。

序列内的数字由小到大排列，不同序列按照首个数字从小到大排列。
示例 1：

输入：target = 9
输出：[[2,3,4],[4,5]]
示例 2：

输入：target = 15
输出：[[1,2,3,4,5],[4,5,6],[7,8]]
```
链接：https://leetcode-cn.com/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof

### 我的AC代码
```
var range = function (start, end) {
    let arr = [];
    for(let i = start; i <= end; i++) {
        arr.push(i);
    }
    return arr;
}
/**
 * @param {number} target
 * @return {number[][]}
 */
var findContinuousSequence = function(target) {
    let halfNum = Math.round(target/2);
    let i = 1, j = 2;
    let res = [];
    while(i <= halfNum) {
        let sum = (i+j)*(j-i+1)/2;
        if( sum === target) {
            res.push(range(i, j));
            j++;
            i++;
        }
        else if(sum < target) {
            j++;
        }
        else {
            i++;
        }
    }
    return res;
};
```

### 解题思路
使用滑动窗口法。
从左往右滑动。当窗口内之和小于target之时，右边界向右滑动；
当窗口内之和大于target之时，左边界向右滑动；
当窗口之和等于target之时，则证明窗口内数组满足条件。下一个满足的条件的右边界一定在当前边界的右侧，因此右边界往右滑动，此时窗口之和肯定大于target了，因此可以将左边届也向右滑动。
直到左边界大于目标值的一半，因为之后的窗口之和一定都大于target。
