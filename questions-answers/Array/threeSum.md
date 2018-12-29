## 两数之和
    给定一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？找出所有满足条件且不重复的三元组。
    注意：答案中不可以包含重复的三元组。  
#### 示例
    给定数组 nums = [-1, 0, 1, 2, -1, -4]，

    满足要求的三元组集合为：
    [
        [-1, 0, 1],
        [-1, -1, 2]
    ]  
#### 思路
    如果随机找C3n种方案。假定满足条件的三个数为a,b,c，这三个数索引分别为i, j, k。先排序，从数组的头确定一个数a，b的索引比a大1，c为数组的尾，有三种情况
    * a + b + c = target 则i++ k-- 并把这三个数记录下来
    * a + b + c < target 则j++
    * a + b + c < target 则k--
    * 终止条件b < c。
    相当于确定两个，动一个，这样比较好确定方案
    首先，这个题我是不会，上面的思路是网上的，参考网上别的语言的思路和答案解出来的，真难- -!，还是解决了。
    1 先排序，说明了最小的在前，负数在前，最大的在后
    2 for循环，三个数，三个下标，以第一个数为i，第二个数和第三个数进行变换，看代码
    3 首个while，说明j<k时，继续下一个循环
    4 第二个while，是为了去重，这两个while都不能用if来判断。因为if会当第一个成立的时候会终止
    5 所谓的j++，k++，是为了移动下标
### 答案  
```  javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var threeSum = function(nums) {
    var total = [];
    nums = nums.sort((a, b) => a - b);
    var len = nums.length;
    for (var i = 0; i < len - 2; i++) {
        if (i > 0 && nums[i - 1] == nums[i]) continue
        var j = i + 1,
            k = len - 1;
        while (j < k) {
            if (nums[i] + nums[j] + nums[k] < 0) {
                // 去重复
                if (nums[j] == nums[j + 1]) {
                    j++;
                }
                j++;
            }
            else if (nums[i] + nums[j] + nums[k] > 0) {
                // 去重复
                if (nums[k] == nums[k - 1]) {
                    k--;
                }
                k--;
            }
            else {
                var result = [];
                result.push(nums[i], nums[j], nums[k]);
                total.push(result);
                // 去重复
                while (nums[j] == nums[j + 1]) {
                    j++;
                }
                while (nums[k] == nums[k - 1]) {
                    k--;
                }
                j++;
                k--;
            }
        }
    }
    return total
};
```