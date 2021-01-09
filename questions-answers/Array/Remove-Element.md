## 移除元素
    给你一个数组 nums 和一个值 val，你需要 原地 移除所有数值等于 val 的元素，并返回移除后数组的新长度。
    不要使用额外的数组空间，你必须仅使用 O(1) 额外空间并 原地 修改输入数组。
    元素的顺序可以改变。你不需要考虑数组中超出新长度后面的元素。

#### 示例1
    给定 nums = [3,2,2,3], val = 3,
    函数应该返回新的长度 2, 并且 nums 中的前两个元素均为 2。
    你不需要考虑数组中超出新长度后面的元素。

#### 示例2
    给定 nums = [0,1,2,2,3,0,4,2], val = 2,

    函数应该返回新的长度 5, 并且 nums 中的前五个元素为 0, 1, 3, 0, 4。

    注意这五个元素可为任意顺序。

    你不需要考虑数组中超出新长度后面的元素。

#### 说明:
    

    为什么返回数值是整数，但输出的答案是数组呢?

    请注意，输入数组是以「引用」方式传递的，这意味着在函数里修改输入数组对于调用者是可见的。

    你可以想象内部操作如下:

        // nums 是以“引用”方式传递的。也就是说，不对实参作任何拷贝
        int len = removeElement(nums, val);

        // 在函数里修改输入数组对于调用者是可见的。
        // 根据你的函数返回的长度, 它会打印出数组中 该长度范围内 的所有元素。
        for (int i = 0; i < len; i++) {
            print(nums[i]);
        }
#### 思路
    题目说：“你不需要考虑数组中超出新长度后面的元素”

    意思就是，你在原数组中进行修改，返回出目标数组的长度，超过这个长度的数组项可以继续留在原数组，长度以内的项就是结果项

```  javascript
/**
 * @param {number[]} nums
 * @param {number} val
 * @return {number}
 */
var removeElement = function(nums, val) {
    let count = 0;
    for(let i = 0;i<nums.length;i++){
        if(nums[i] !== val){
            nums[count] = nums[i]
            count++
        }
    }
    return count;
};
```

#### 思路2
    双指针
    * 指向头尾的双指针
    * 遇到等于val的项，就拿数组的末尾项覆盖它
    * 末尾项搬到前面来了，将尾指针左移一位
    * 如果遇到不同于val的项，左指针就+1，考察下一项
    * 循环结束的条件是两个指针交叉相遇
#### 答案2
```  javascript
/**
 * @param {number[]} nums
 * @param {number} val
 * @return {number}
 */
var removeElement = function(nums, val) {
    let index = 0, last = nums.length - 1
    while (index <= last) {
        if (nums[index] === val) {
            nums[index] = nums[last]
            last--
        } else {
            index++
        }
    }
    return index
};
```

#### 思路3
    splice 删除元素
    * 遇到和val相同的，直接删除，导致后面的项前移一位
    * 指针 i 要 -1，考察前移过来的新来的项，不然会漏掉考察它
#### 答案3
```  javascript
/**
 * @param {number[]} nums
 * @param {number} val
 * @return {number}
 */
var removeElement = (nums, val) => {
  for (let i = 0; i < nums.length; i++) {
    if (nums[i]===val) {
      nums.splice(i, 1)
      i--
    }
  }
  return nums.length
}
```
