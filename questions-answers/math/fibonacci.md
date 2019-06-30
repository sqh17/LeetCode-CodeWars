## 斐波那契数列
    用 JavaScript 实现斐波那契数列函数,返回第n个斐波那契数。 f(1) = 1, f(2) = 1 等
    
#### 示例
    1、1、2、3、5、8、13、21、34、……
#### 思路
    从第三个开始，该数是前两个数的和
### 答案1
```  javascript
fibonacci(n){
    if(n==1 | n== 2){
        return 1
    }else{
        return fibonacci(n - 1) + fibonacci(n - 2) 
    }
}
```
### 答案2
```  javascript
function fibonacci(n){
  if(n == 1 || n == 2 ){
    return 1
  }else{
    var current = 0; // 第三个
    var first = 1;  
    var second = 1;
    for(var i = 2;i<n;i++){
      current = first + second // 当前是前两个的和
      first = second // 之后第一个数就变成了之前的第二个数
      second = current // 之后第二个数就变成了之前的第三个数
      
    }
    return current
  }
}
```