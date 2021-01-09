## 长度最小的子数组
  含有 n 个正整数的数组和一个正整数 s ，找出该数组中满足其和 ≥ s 的长度最小的 连续 子数组，并返回其长度。如果不存在符合条件的子数组，返回 0。
#### 示例
  输入：s = 7, nums = [2,3,1,2,4,3]
  输出：2
  解释：子数组 [4,3] 是该条件下的长度最小的子数组。

#### 思路
滑动窗口
* 连续子数组可以表示为 [i,j][i,j]：从第 i 项到第 j 项。
* 当 [i,j][i,j] 子数组和 >= s，如果此时扩张窗口，条件依然满足，但背离“最小长度”的要求。
  * 所以选择收缩窗口，i 右移，直到条件不再满足（这里是一个循环），这是在优化可行解，并让窗口长度挑战最小纪录。
* 当窗口的和 < s，此时应该扩张窗口，j 右移，直到条件重新满足。
#### 答案
```  javascript
/**
 * @param {number} s
 * @param {number[]} nums
 * @return {number}
 */
const minSubArrayLen = (s, nums) => {
  let minLen = Infinity;
  let i = 0;
  let j = 0;
  let sum = 0;
  while (j < nums.length) {   // 主旋律是扩张，找可行解
    sum += nums[j];
    while (sum >= s) {        // 间歇性收缩，优化可行解
      minLen = Math.min(minLen, j - i + 1);
      sum -= nums[i];
      i++;
    }
    j++;
  }
  // for(;j<nums.length;j++){
  //   sum += nums[j];
  //   while(sum >= s){
  //     minLen = Math.min(minLen, j - i +1);
  //     sum -= nums[i++]; // i++ 先计算后加1
  //   }
  // }
  return minLen === Infinity ? 0 : minLen; // 从未找到可行解，返回0
};
```