## 最长递增子序列

    给你一个整数数组 nums ，找到其中最长严格递增子序列的长度。

    子序列 是由数组派生而来的序列，删除（或不删除）数组中的元素而不改变其余元素的顺序。例如，[3,6,2,7] 是数组 [0,3,1,6,2,2,7] 的子序列。

#### 示例1

    输入：nums = [10,9,2,5,3,7,101,18]
    输出：4
    解释：最长递增子序列是 [2,3,7,101]，因此长度为 4 。

#### 示例2

    输入：nums = [0,1,0,3,2,3]
    输出：4

#### 示例3

    输入：nums = [7,7,7,7,7,7,7]
    输出：1

### 思路1-动态规划

    1. 初始化一个长度相当的数组，用1填充，因为最短的子序列为1，两次循环
    2. 每次进行比较dp的值，获得符合条件的数值时，比较dp的大小
    注意：不是取比当前元素小的总元素，必须严格按从小到大的顺序，所以需要去比较dp.
    比如 2 5 3 7 这一段，dp最大是3，因为组合2 5 7 或2 3 7

### 答案1

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var lengthOfLIS = function(nums) {
    if(nums.length<=0) return 0
    let dp = new Array(nums.length).fill(1)
    for (let i = 0; i < nums.length; i++) {
        for (let j = 0; j < i; j++) {
            if (nums[j] < nums[i]) {
                dp[i] = Math.max(dp[i], dp[j] + 1)
            }
        }
    }
    return Math.max(...dp)
};
```

### 答案2-贪心+二分查找

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var lengthOfLIS = function(nums) {
  let arr = nums
  const len = arr.length
  const min_arr = [0] // 存储最小的索引，以索引0为基准
  const prev_arr = arr.slice() // 储存前面的索引，slice为浅复制一个新的数组
  let last_index
  let start
  let end
  let middle
  for (let i = 0; i < len; i++) {
    let arrI = arr[i]
    // 1. 如果当前n比min_arr最后一项大
    last_index = min_arr[min_arr.length - 1]
    if (arr[last_index] < arrI) {
      min_arr.push(i)
      prev_arr[i] = last_index // 前面的索引
      continue
    }
    // 2. 如果当前n比min_arr最后一项小（二分类查找）
    start = 0
    end = min_arr.length - 1
    while(start < end) {
      middle = (start + end) >> 1 // 相当于Math.floor((start + end)/2)
      if (arr[min_arr[middle]] < arrI) {
        start = middle + 1
      } else  {
        end = middle
      }
    }
    if (arr[min_arr[end]] > arrI) {
      min_arr[end] = i
      if (end > 0) {
        prev_arr[i] = min_arr[end - 1] // 前面的索引
      }
    }
  }

  // 从最后一项往前查找
  let result = []
  let i = min_arr.length
  let last = min_arr[i - 1]
  while(i-- > 0) {
    result[i] = last
    last = prev_arr[last]
  }

  return result.length
};
```
