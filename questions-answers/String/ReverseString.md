## 翻转字符串
  请编写一个函数，其功能是将输入的字符串反转过来。 
#### 示例1
    输入：s = "hello"
    返回："olleh"
### 答案  
```  javascript
/**
 * @param {string} s
 * @return {string}
 */
var reverseString = function(s) {
    return s.split('').reverse().join('');
};
```
