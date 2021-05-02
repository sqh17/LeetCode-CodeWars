## 平方数之和
    给定一个非负整数 c ，你要判断是否存在两个整数 a 和 b，使得 a2 + b2 = c 。
#### 示例1
    输入：c = 5
    输出：true
    解释：1 * 1 + 2 * 2 = 5
#### 示例2
    输入：c = 3
    输出：false
#### 示例3
    输入：c = 4
    输出：true
### 答案1
```  javascript
/**
 * @param {number} c
 * @return {boolean}
 */
var judgeSquareSum = function(c) {
    for (let a = 0; a * a <= c; a++) {
        const b = Math.sqrt(c - a * a);
        if (b === parseInt(b)) {
            return true;
        }
    }
    return false;
};
```
### 答案2
```  javascript
/**
 * @param {number} c
 * @return {boolean}
 */
var judgeSquareSum = function(c) {
    let left = 0;
    let right = Math.floor(Math.sqrt(c));
    while(left <= right){
        const sum = left * left + right * right;
        if(sum === c){
            return true
        }else if(sum > c){
            right --
        }else if(sum < c){
            left ++
        }
    }
};
```