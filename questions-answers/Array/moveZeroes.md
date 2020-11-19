## 移动零
    给定一个数组 nums，编写一个函数将所有 0 移动到数组的末尾，同时保持非零元素的相对顺序。 
#### 示例
    输入: [0,1,0,3,12]
    输出: [1,3,12,0,0] 
#### 说明
    * 必须在原数组上操作，不能拷贝额外的数组。
    * 尽量减少操作次数。
### 答案  
```  javascript
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function(nums) {
    var count = 0
    for(var i = 0;i<nums.length;i++){
        if(nums[i] == 0){
            nums.splice(i,1);
            i--
            count++
        }
    }
    for(var j = 0;j<count;j++){
        nums.push(0)
    }
    console.log(nums)
    return nums
};
```
### 思路2
while 跑一遍，执行到等于 0 的时候，拔掉该 0，最后推 0，从同个地方再找；如果不是 0，继续找下一个。
### 答案2
```  javascript
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function(nums) {
    let count = 0
    let idx = 0
    while(count < nums.length) {
        if(nums[idx] === 0) {
            nums.splice(idx, 1)
            nums.push(0)
        }
        else idx += 1
        count += 1
    }
};
```