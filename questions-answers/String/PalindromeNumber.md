## 翻转字符串
  判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。 
#### 示例1
    输入: 121
    输出: true
#### 示例2
    输入: -121
    输出: false
    解释: 从左向右读, 为 -121 。 从右向左读, 为 121- 。因此它不是一个回文数。
#### 示例3
    输入: 10
    输出: false
    解释: 从右向左读, 为 01 。因此它不是一个回文数。
### 答案  
```  javascript
/**
 * @param {number} x
 * @return {boolean}
 */
var isPalindrome = function(x) {
    if(x < 0 || (x % 10 == 0 && x != 0)) {
        return false;
    }
    var res = x.toString().split('').reverse().join('');
    if(x.toString() == res){
        return true
    }else{
        return false;
    }  
};
```
