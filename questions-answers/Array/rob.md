## 打家劫舍
    你是一个专业的小偷，计划偷窃沿街的房屋。每间房内都藏有一定的现金，影响你偷窃的唯一制约因素就是相邻的房屋装有相互连通的防盗系统，如果两间相邻的房屋在同一晚上被小偷闯入，系统会自动报警。

    给定一个代表每个房屋存放金额的非负整数数组，计算你 不触动警报装置的情况下 ，一夜之内能够偷窃到的最高金额。
#### 示例1
    输入: [1,2,3,1]
    输出: 4
    解释: 偷窃 1 号房屋 (金额 = 1) ，然后偷窃 3 号房屋 (金额 = 3)。
        偷窃到的最高金额 = 1 + 3 = 4 。
#### 示例2
    输入: [2,7,9,3,1]
    输出: 12
    解释: 偷窃 1 号房屋 (金额 = 2), 偷窃 3 号房屋 (金额 = 9)，接着偷窃 5 号房屋 (金额 = 1)。
        偷窃到的最高金额 = 2 + 9 + 1 = 12 。
### 答案1  
```  javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var rob = function(nums) {
    if(nums.length == 0) return 0
    if(nums.length == 1) return nums[0];
    if(nums.length == 2) return Math.max(nums[0],nums[1]);
    if(nums.length == 3) return Math.max(nums[1],nums[0] + nums[2]);
    let dp = [];
    dp[0] = nums[0],dp[1] = Math.max(nums[0],nums[1]),dp[2] = Math.max(nums[1],nums[0] + nums[2]);
    for(var i = 3;i<nums.length;i++){
        dp[i] = Math.max(dp[i - 1],nums[i] + dp[i - 2])
    }
    return Math.max(dp[nums.length - 1],dp[nums.length - 2]);
};
```

### 答案2  （空间优化）
```  javascript
// i 其实只依赖于 i - 1 和 i - 2 两个状态，因此我们其实不需要定义一个长度为 n 的 dp 数组，只要定义两个变量来存储 i - 1 和 i - 2 不就行了嘛，于是这样就把空间优化到了 O(1)

// 参照着 dp[i] = max(dp[i - 1], dp[i - 2] + nums[i]) 这个方程来写，用 a 表示 i - 2，b 表示 i - 1，因此上面的方程变成了dp[i] = max(b, a + nums[i])，
var rob = function(nums) {
    var a = 0, b = 0;
    for (var i = 0; i < nums.length; i++) {
        var c = Math.max(b, a + nums[i]);
        a = b;
        b = c;
    }
    return b;
};
```