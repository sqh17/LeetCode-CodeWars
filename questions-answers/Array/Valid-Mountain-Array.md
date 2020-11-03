## 有效的山脉数组
    给定一个整数数组 A，如果它是有效的山脉数组就返回 true，否则返回 false。

    让我们回顾一下，如果 A 满足下述条件，那么它是一个山脉数组：
    * A.length >= 3
    * 在 0 < i < A.length - 1 条件下，存在 i 使得：
        * A[0] < A[1] < ... A[i-1] < A[i]
        * A[i] > A[i+1] > ... > A[A.length - 1]
#### 示例1
    输入：[2,1]
    输出：false

#### 示例2
    输入：[3,5,5]
    输出：false

#### 示例3
    输入：[0,3,2,1]
    输出：true   

#### 思路
    双指针法
    让首尾两个指针去爬山。
    左指针能爬高，就右移。
    右指针能爬高，就左移。
    当指针相遇时，指向的元素就是山顶。
    但要保证这个山顶不处在数组两端。即，两个指针必须经历爬高阶段，才齐聚山顶。
    这也排除了数组长度小于 3 的情况，因为我们至少有左右端点和山顶，三个点。
```  javascript
/**
 * @param {number[]} A
 * @return {boolean}
 */
var validMountainArray = function(A) {
    if(A.length < 3) return false
    let i = 0,j = A.length - 1;
    while(i + 1 < A.length && A[i]<A[i+1]){
        i++
    }
    while(j - 1 > 0 && A[j] < A[j-1]){
        j--
    }
    if(i !== 0 && i === j && j !== A.length - 1){
        return true
    }
    return false
};
```