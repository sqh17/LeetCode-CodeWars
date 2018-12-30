## IQTest
  to find out which one of the given numbers differs from the others ,a program that among the given numbers finds one that is different in evenness, and return a position of this number.
  编写一个函数，找出一个字符串中的不一样的数的位置，就是奇偶数。
#### 示例1
    iqTest("2 4 7 8 10") => 3 // Third number is odd, while the rest of the numbers are even
#### 示例2
    iqTest("1 2 1 1") => 2 // Second number is even, while the rest of the numbers are odd
### 思路
    1 将字符串转化为数组
    2 声明变量，奇数数组，偶数数组，奇数位置，偶数位置
    3 for遍历，当判断除2余数得知，存数据
    4 根据奇数数组和偶数数组的个数，返回位置（索引）
### 答案1
```  javascript
function iqTest(numbers) {
    var arr = numbers.split(' ');
    var odd=[],even=[],oddIndex = null, evenIndex =null;
    for (var i = 0; i < arr.length; i++) {
        if (arr[i] % 2 == 0) {
            odd.push(arr[i]);
            oddIndex = i+1;
        } else {
            even.push(arr[i])
            evenIndex = i+1;
        }
    }
    if (odd.length > even.length) {
        return evenIndex
    } else {
        return oddIndex
    }
}
```
### 答案2
```javascript
// array.map()返回return之后的数组
// array.filter() 返回的是一个数组
function iqTest(numbers){
  numbers = numbers.split(" ").map(function(el){return parseInt(el)});
  
  var odd = numbers.filter(function(el){ return el % 2 === 1});
  var even = numbers.filter(function(el){ return el % 2 === 0});
  
  return odd.length < even.length ? (numbers.indexOf(odd[0]) + 1) : (numbers.indexOf(even[0]) + 1);
}
```
