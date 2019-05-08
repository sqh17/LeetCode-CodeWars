## covertString
    Complete the function/method so that it takes CamelCase string and returns the string in snake_case notation. Lowercase characters can be numbers. If method gets number, it should return string.
    请完成一个函数／方法，将驼峰命名的字符串转化成用_连接的字符串，如果是一个数字，则转化成字符串
#### 示例1
    //  returns test_controller
    toUnderscore('TestController');
#### 示例2
    // returns movies_and_books
    toUnderscore('MoviesAndBooks');
#### 示例3
    // returns app7_test
    toUnderscore('App7Test');
#### 示例4
    // returns "1"
    toUnderscore(1);
#### 思路
    1. 首先判断是不是数字
    2. 利用正则在大写单词前加_并化成小写
    3. 截取字符串
### 答案1 
```  javascript
function toUnderscore(string) {
  // TODO: complete
  if (!(isNaN(string) || parseInt(string).toString() == 'NaN')) return string
  string = string.replace(/[A-Z]/g,function(str){
    return `_${str.toLowerCase()}`
  })
  return string.substring(1,string.length)
}
```
### 答案2
```  javascript
var toUnderscore;
toUnderscore = function(string) {
  return string.toString().split(/(?=[A-Z])/).join('_').toLowerCase();
};
```
### 答案3
```javascript
function toUnderscore(string) {
  return (''+string).replace(/(.)([A-Z])/g, '$1_$2').toLowerCase();
}
```
