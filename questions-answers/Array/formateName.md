## Format a string of names.
    Given: an array containing hashes of names
    Return: a string formatted as a list of names separated by commas except for the last two names, which should be separated by an ampersand.
    请编写一个函数，在一个数组对象中，按要求返回名字格式，看例子
#### 示例1
    输入：list([ {name: 'Bart'}, {name: 'Lisa'}, {name: 'Maggie'} ])
    返回：'Bart, Lisa & Maggie'
#### 示例2
    输入：list([ {name: 'Bart'}, {name: 'Lisa'} ])
    返回：'Bart & Lisa'
#### 示例3
    输入：list([ {name: 'Bart'} ])
    返回：'Bart'
#### 示例4
    输入：list([])
    返回：''
### 答案1 
```  javascript
function list(names){
  //your code here
  if(names.length == 0) return '';
  var res = names.map(val=>val.name);
  var str = '';
  if(res.length == 1){
      str = res.join();
  }else if(res.length == 2){
      str = res.join(' & ');
  }else{
      var last = `& ${res.pop()}`;
      str = `${res.join(', ')} ${last}`
  }
  return str;
}
```
### 答案2
```  javascript
function list(names){
  return names.reduce(function(prev, current, index, array){
    if (index === 0){
      return current.name;
    }
    else if (index === array.length - 1){
      return prev + ' & ' + current.name;
    } 
    else {
      return prev + ', ' + current.name;
    }
  }, '');
}
```
### 答案3
```  javascript
var list = (names) =>  names.map(x => x.name).join(', ').replace(/(.*),(.*)$/, "$1 &$2")
```
