## 两数之和
  给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。(不使用额外空间)  
#### 示例1
    输入: [2,2,1]
    输出: 1 
#### 示例2
    输入: [4,1,2,1,2]
    输出: 4
#### 思路
    1 要求不能用额外空间
    2 数学方法：异或，所有相同的为0，不同为1
    3 for循环，依次异或。
    4 返回该值
### 答案  
```  javascript
//**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
    var res = 0
    for(var i = 0;i<nums.length;i++){
        res ^= nums[i];
    }
    return res
};
```