## 删除排序数组中的重复项
  给定一个排序数组，你需要在原地删除重复出现的元素，使得每个元素只出现一次，返回移除后数组的新长度。
  不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。 
#### 示例1
    给定数组 nums = [1,1,2], 
    函数应该返回新的长度 2, 并且原数组 nums 的前两个元素被修改为 1, 2。 
    你不需要考虑数组中超出新长度后面的元素。
#### 示例2
    给定 nums = [0,0,1,1,1,2,2,3,3,4],
    函数应该返回新的长度 5, 并且原数组 nums 的前五个元素被修改为 0, 1, 2, 3, 4。
    你不需要考虑数组中超出新长度后面的元素。
### 答案1
```  javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var removeDuplicates = function(nums) {
    if (nums.length == 0) return 0;
    for (var j = 1, i = 0; j < nums.length; j++) {
        if (nums[j] != nums[i]) {
            i++;
            nums[i] = nums[j];
        }
    }
    return i + 1;
};
```
### 答案2
```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var removeDuplicates = function(nums) {
  let j = 0;
  for(let i = 0;i<nums.length;i++)
  {
    if(nums[i] !== nums[i+1]){
      nums[j++] = nums[i];
    }
  }
  return j
};
```
### 答案3 （时间复杂度最高）
```javascript
var removeDuplicates = function (nums) {
    var cur = nums[0];
    for (var i = 1; i < nums.length;) {
        if (nums[i] === cur)
            nums.splice(i, 1);
        else
            cur = nums[i++];
    }
    return nums.length
};
```
