## WeIrD StRiNg CaSe
    一堆英文，概括为，给一个字符串，让每一个字符的索引偶数项为小写字母，奇数项为大写字母  
#### 示例
    'This is a test'   ==> 'ThIs Is A TeSt'
    'this' ==> 'ThIs' 
### 答案  
```  javascript
 function toWeirdCase(string) {
    var resStr =  string.split(' ').map((v) => {
       return v.split('').map((value,index)=>{
        return index%2 == 0?value.toUpperCase():value.toLowerCase()
       }).join('')
    }).join(' ')
    console.log(resStr)
    return resStr;
}
```
