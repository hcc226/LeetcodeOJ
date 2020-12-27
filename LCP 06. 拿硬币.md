### 题目描述
```
桌上有 n 堆力扣币，每堆的数量保存在数组 coins 中。我们每次可以选择任意一堆，拿走其中的一枚或者两枚，求拿完所有力扣币的最少次数。

示例 1：

输入：[4,2,1]

输出：4

解释：第一堆力扣币最少需要拿 2 次，第二堆最少需要拿 1 次，第三堆最少需要拿 1 次，总共 4 次即可拿完。

示例 2：

输入：[2,3,10]

输出：8

限制：

1 <= n <= 4
1 <= coins[i] <= 10
```
链接：https://leetcode-cn.com/problems/na-ying-bi

### 我的AC代码
```
/**
 * @param {number[]} coins
 * @return {number}
 */
var minCount = function(coins) {
    let coinsArray = new Array(11);
    coinsArray[1] = 1;
    coinsArray[2] = 1;
    for (let i = 3; i <= 11; i++) {
        coinsArray[i] =  Math.min(coinsArray[i - 1], coinsArray[i - 2]) + 1;
    }

    let res = 0;
    for(let i = 0;i < coins.length; i++) {
        res += coinsArray[coins[i]];
    }
    return res;
};
```

### 题解思路
此题也是一个简单的动态规划，我使用coinsArray来存储数量为i的硬币被拿完所用的次数
```
coinsArray[1] = 1;
coinsArray[2] = 1;
coinsArray[i] =  Math.min(coinsArray[i - 1], coinsArray[i - 2]) + 1;
```
以此得到每个数字数量的硬币所用的次数。

然后，对于coins中的每个数字，得到的次数相加即为最后的结果。
