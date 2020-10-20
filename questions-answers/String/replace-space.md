## 替换空格
    请实现一个函数，把字符串 s 中的每个空格替换成"%20"。
#### 示例
    输入：s = "We are happy."
    输出："We%20are%20happy."
    0 <= s 的长度 <= 10000
    
### 答案1
```  javascript
/**
 * @param {string} s
 * @return {string}
 */
var replaceSpace = function(s) {
    return s.replace(/\s/g,'%20')
};
```
### 答案2
```  javascript
/**
 * @param {string} s
 * @return {string}
 */
var replaceSpace = function(s) {
    if(s.length>= 0 && s.length<= 10000 && typeof s === 'string'){
        return s.split(' ').join('%20')
    }else{
        return ''
    }
    
};
```