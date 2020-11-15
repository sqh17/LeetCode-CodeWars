## 按奇偶排序数组 II
    给定一个非负整数数组 A， A 中一半整数是奇数，一半整数是偶数。
    对数组进行排序，以便当 A[i] 为奇数时，i 也是奇数；当 A[i] 为偶数时， i 也是偶数。
    你可以返回任何满足上述条件的数组作为答案。
#### 示例
    输入：[4,2,5,7]
    输出：[4,5,2,7]
    解释：[4,7,2,5]，[2,5,4,7]，[2,7,4,5] 也会被接受。
### 答案1  
```  javascript
/**
 * @param {number[]} A
 * @return {number[]}
 */
var sortArrayByParityII = function(A) {
    let oddArr = A.filter(i => i % 2 !== 0);
    let evenArr = A.filter(i => i % 2 === 0);
    let arr = [];
    while(oddArr.length || evenArr.length){
        arr.push(evenArr.pop());
        arr.push(oddArr.pop());
    }
    return arr;
};
```

### 思路2 
    双指针 
    为数组的偶数下标部分和奇数下标部分分别维护指针 i, ji,j。随后，在每一步中，如果 A[i]A[i] 为奇数，则不断地向前移动 jj（每次移动两个单位），直到遇见下一个偶数。此时，可以直接将 A[i]A[i] 与 A[j]A[j] 交换。我们不断进行这样的过程，最终能够将所有的整数放在正确的位置上。
### 答案2  
```  javascript
const swap = (A, i, j) => {
    const temp = A[i];
    A[i] = A[j];
    A[j] = temp;
};
var sortArrayByParityII = function(A) {
    const n  = A.length;
    let j = 1;
    for (let i = 0; i < n; i += 2) {
        if (A[i] & 1) {
            while (A[j] & 1) {
                j += 2;
            }
            swap(A, i, j);
        }
    }   
    return A;
};
```