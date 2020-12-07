## 在排序数组中查找元素的第一个和最后一个位置

    给定一个按照升序排列的整数数组 nums，和一个目标值 target。找出给定目标值在数组中的开始位置和结束位置。
    如果数组中不存在目标值 target，返回 [-1, -1]。

    进阶：
    你可以设计并实现时间复杂度为 O(log n) 的算法解决此问题吗？
#### 示例1
    输入：nums = [5,7,7,8,8,10], target = 8
    输出：[3,4]

#### 示例2
    输入：nums = [5,7,7,8,8,10], target = 6
    输出：[-1,-1]

#### 示例3
    输入：nums = [], target = 0
    输出：[-1,-1] 

#### 示例4
    输入：nums = [1], target = 1
    输出：[0,0] 
#### 答案1
```  javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var searchRange = function(nums, target) {
    if(nums.length === 0) return [-1,-1];
    if(nums.indexOf(target) == -1) return [-1,-1]
    let arr = [nums.indexOf(target)];
    for(let i = nums.length - 1;i >= nums.indexOf(target);i--){
        if(nums[i] === target){
            arr.push(i)
            break
        }
    }
    return arr;
};
```
#### 答案2
```  javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var searchRange = function(nums, target) {
    return [nums.indexOf(target),nums.lastIndexOf(target)]
};
```
#### 思路3 
    1. 二分查找
    2. 如果 lower 为 true，则查找第一个大于等于 target 的下标，否则查找第一个大于 target 的下标。
    3. 因为target 可能不存在数组中，因此我们需要重新校验我们得到的两个下标 leftIdx 和 rightIdx，看是否符合条件，如果符合条件就返回 [leftIdx,rightIdx]，不符合就返回 [-1,-1]
#### 答案3
```  javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
let binarySearch = function(nums,target,lower){
    let left = 0, right = nums.length - 1, ans = nums.length;
    while(left<=right){
        const mid = Math.floor((left + right) / 2);
        if(nums[mid] > target || (nums[mid] >= target && lower)){
            right = mid - 1;
            ans = mid;
        }else{
            left = mid + 1;
        }
    }
    return ans
}
var searchRange = function(nums, target) {
    let res = [-1,-1];
    let leftIndex = binarySearch(nums,target,true);
    let rightIndex = binarySearch(nums,target,false) - 1;
    if(leftIndex <= rightIndex && nums[leftIndex] == target && nums[rightIndex] == target && rightIndex < nums.length){
        res = [leftIndex,rightIndex]
    };
    return res;
};
```