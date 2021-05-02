## 合并两个有序数组
给你两个有序整数数组 nums1 和 nums2，请你将 nums2 合并到 nums1 中，使 nums1 成为一个有序数组。
说明：
	初始化 nums1 和 nums2 的元素数量分别为 m 和 n 。
	你可以假设 nums1 有足够的空间（空间大小大于或等于 m + n）来保存 nums2 中的元素。

#### 示例

	输入：
	nums1 = [1,2,3,0,0,0], m = 3
	nums2 = [2,5,6],       n = 3

	输出：[1,2,2,3,5,6]

#### 思路

双指针, 从后边挨个对比, 大的放后边
注意一下边界条件: 当其中有个数组都放完了, 就不需要判断大小了, 直接把另一个数组的 挨个从后放

#### 答案

```javascript

/**
 * @param {number[]} nums1
 * @param {number} m
 * @param {number[]} nums2
 * @param {number} n
 * @return {void} Do not return anything, modify nums1 in-place instead.
 */
var merge = function(nums1, m, nums2, n) {
let i = nums1.length - 1
  m = m - 1
  n = n - 1         // 因为m 和 n 是长度, 现在把它们当成索引
  while (i >= 0) {
    if((m >= 0 && nums1[m] < nums2[n]) || m < 0){
      nums1[i--] = nums2[n--]           // 赋值后, i 和 n 才减1
    } else {
      nums1[i--] = nums1[m--]
    }
  }
};
```