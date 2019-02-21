## sum-Pairs.
    给一个数组和数字，求数组的第一个两个数相加数字的数组
#### 示例1
    输入: [4, 3, 2, 3, 4], 6
    输出: [4,2]
#### 示例2
    输入: [11, 3, 7, 5],         10
    输出: [3,7]
#### 示例3
    输入: [0, 0, -2, 3], 2
    输出: undefined
#### 示例4
    输入: [10, 5, 2, 3, 7, 5],         10
    输出: [5,5]

### 答案1(超时，不算完成)
```  javascript
function sum_pairs(ints,s){
    var arr = [];
    for(var i = 0;i<ints.length;i++){
        for(var j = i + 1;j<ints.length;j++){
            if(ints[i] + ints[j] == s){
                arr=[ints[i],ints[j]];
                ints.length = j;
            }
        }
    }
    return arr.length != 0 ? arr:undefined
}
```

### 答案2
```  javascript
var sum_pairs=function(ints, s){
    var seen = {}
    for (var i = 0; i < ints.length; ++i) {
        if (seen[s - ints[i]]) return [s - ints[i], ints[i]];
        seen[ints[i]] = true
    }
}
```

### 答案3 
```  javascript
function sum_pairs(ints, s) {
  let seen = new Set();
  for (let i of ints) {
    if (seen.has(s - i)) return [s - i, i];
    seen.add(i);
  }
}
```
