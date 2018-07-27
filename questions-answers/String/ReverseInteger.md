## 翻转字符串
  给定一个 32 位有符号整数，将整数中的数字进行反转。 
#### 示例1
    输入: 123
    输出: 321
#### 示例2
    输入: -123
    输出: -321
#### 示例3
    输入: 120
    输出: 21
### 思路
    1 先判断整数是否正数
    2 若是正数，先化成字符串->数组->反转->数字
    3 若是负数，先化成字符串->数组,切割符号，返回一个新数组，->反转->数字
    4 最后要判断一下是否为32位
### 答案  
```  javascript
/**
 * @param {number} x
 * @return {number}
 */
var reverse = function(x) {
    var res;
    if(x >= 0){
        var arr = x.toString().split('');
        res = Number(arr.reverse().join(''));
    }else{
        var arr = x.toString().split('')
        var arr1 = arr.splice(1,arr.length);
        res = Number(-arr1.reverse().join(''));
    }
    if(res > 2 ** 31 - 1 || res < -(2 ** 31)){
        return 0
    }else{
        return res
    }
    
};
```
