## Find the unique number
    找到一个数组中不重复的一个元素， 
#### 示例
    输入: [ 1, 1, 1, 2, 1, 1 ]
    输出: 2
### 答案1
```  javascript
function findUniq(arr) {
  // do magic
 
  for(var i = 0;i<arr.length;i++){
   var count = 0;
    for(var j = 0;j<arr.length;j++){
      if(arr[i] == arr[j]){
        count++
      }
      if(count > 1){
        break
      }
    }
    if(count == 1){
      return arr[i]
    }
  }
}
```
### 答案2
```  javascript
function findUniq(arr) {
  var res = arr.sort((a,b)=>a-b);
  return res[0] == res[1]?res.pop():res[0]
}
```
### 答案3
```  javascript
function findUniq(arr) {
  return arr.find(n=>arr.indexOf(n) == arr.lastIndexOf(n))
}
```
### 答案4
```javascript
function findUniq(arr) {
  let [a,b,c] = arr.slice(0,3);
  if( a != b && a!=c ) return a;
  for( let x of arr ) if( x!=a ) return x
}
```