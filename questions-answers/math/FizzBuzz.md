## 删除排序数组中的重复项
    写一个程序，输出从 1 到 n 数字的字符串表示。
    1. 如果 n 是3的倍数，输出“Fizz”；
    2. 如果 n 是5的倍数，输出“Buzz”；
    3.如果 n 同时是3和5的倍数，输出 “FizzBuzz”。 
#### 示例1
    n = 1,
    ["1"]
#### 示例2
    n = 15,
    ["1", "2", "Buzz", "4", "Fizz", "Buzz", "7", "8", "Buzz", "Fizz", "11", "Buzz", "13", "14", "FizzBuzz", "16", "17", "Buzz", "19", "Fizz"]
### 答案  
```  javascript
/**
 * @param {number} n
 * @return {string[]}
 */
var fizzBuzz = function(n) {
    var arr =[];
    for(var i = 1; i < n+1;i++ ){
        arr.push(i.toString());
    };
    arr.map((v,i)=>{
        if( v % 5 == 0){
            if(v % 3 == 0){
                arr.splice(i,1,'FizzBuzz')
            }else{
                arr.splice(i,1,'Buzz')
            } 
        }else if(v %3  == 0){
            arr.splice(i,1,'Fizz')
        }
    })
    return arr
};
```