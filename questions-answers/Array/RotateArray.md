## 两数之和
  给定一个数组，将数组中的元素向右移动 k 个位置，其中 k 是非负数。  
#### 示例1
    输入: [1,2,3,4,5,6,7] 和 k = 3
    输出: [5,6,7,1,2,3,4]
    解释:
    向右旋转 1 步: [7,1,2,3,4,5,6]
    向右旋转 2 步: [6,7,1,2,3,4,5]
    向右旋转 3 步: [5,6,7,1,2,3,4]  
#### 示例2
    输入: [-1,-100,3,99] 和 k = 2
    输出: [3,99,-1,-100]
    解释: 
    向右旋转 1 步: [99,-1,-100,3]
    向右旋转 2 步: [3,99,-1,-100] 
### 思路
    1 通过创建新的数组
    2 先把要移动的数字按顺序存到新数组中（通过一个account记录存了几次）
    3 再把没有移动的数字也存到新数组中。（因为account记录了移动的次数，所以再存时会继续存，而不是从0存）
    4 再还原到原数组中。
### 答案  
```  javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var rotate = function(nums, k) {
    var len = nums.length;
    var res = [];
    var account = 0;
    for(var i = len - k%len;i < len;i++){
        res[account++] = nums[i];
    }
    for(var i = 0; i < len - k%len; i++){
        res[account++] = nums[i];
    }
    for(var i = 0;i < len; i++){
        nums[i] = res[i];
    }

};
```