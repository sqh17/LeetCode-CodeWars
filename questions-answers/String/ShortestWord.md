## shortestWord
    Simple, given a string of words, return the length of the shortest word(s).
    String will never be empty and you do not need to account for different data types 
    给一个英文句子，找到这些里面最短长度的单词，（字符串不是空的，也不需要考虑其他不同的数据类型）
#### 示例1
    "bitcoin take over the world maybe who knows perhaps" => 3
#### 示例2
    "i want to travel the world writing code one day" => 1
### 答案1
```  javascript
function findShort(s) {
    var arr = s.split(' ');
    var resArr = [];
    for(var i = 0;i<arr.length;i++){
        resArr.push(arr[i].length)
    }
    resArr = resArr.sort((a,b)=>a-b)
    return resArr[0]
}
```
### 答案2
```  javascript
function findShort(s){
  return Math.min.apply(null, s.split(' ').map(w => w.length));
}
```
### 答案3
```javascript
const findShort = (s) => s
  .split(' ')
  .sort((a, b) => b.length - a.length)
  .pop()
  .length;
```