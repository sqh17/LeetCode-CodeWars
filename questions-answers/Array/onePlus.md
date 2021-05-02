## 加一
    给定一个由 整数 组成的 非空 数组所表示的非负整数，在该数的基础上加一。
    最高位数字存放在数组的首位， 数组中每个元素只存储单个数字。
    你可以假设除了整数 0 之外，这个整数不会以零开头。
### 示例1
    输入：digits = [1,2,3]
    输出：[1,2,4]
    解释：输入数组表示数字 123。
### 示例2
    输入：digits = [4,3,2,1]
    输出：[4,3,2,2]
    解释：输入数组表示数字 4321
### 示例3
    输入：digits = [0]
    输出：[1]
### 思路1
    先转字符串再加一再转数组，需要考虑临界值，整型溢出的情况。需要研究BigInt。
### 答案1  
```  javascript
/**
 * @param {number[]} digits
 * @return {number[]}
 */
var plusOne = function(digits) {
    let num = BigInt(digits.join(''));
    return (num + BigInt(1)).toString().split('');
};
```

### 思路2
    三种情况：
        1. 末尾无进位
        2. 末尾有进位，在中间位置进位停止，则需要找到进位的典型标志，即为当前位 %10后为 0，则前一位加 1，直到不为 0 为止
        3. 末位有进位，并且一直进位到最前方导致结果多出一位
### 答案2  
```  javascript
/**
 * @param {number[]} digits
 * @return {number[]}
 */
var plusOne = function(digits) {
    let len = digits.length;
    for(var i = len - 1;i>= 0;i--){
        digits[i]++;
        digits[i] %= 10; 
        if(digits[i] !== 0){
            return digits;
        }
    }
    digits.unshift(1);
    return digits;
};
```