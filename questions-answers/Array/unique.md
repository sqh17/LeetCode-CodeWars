## 去重
    为 Array 对象添加一个去除重复项的方法
#### 示例
    输入 \[false, true, undefined, null, NaN, 0, 1, {}, {}, 'a', 'a', NaN]

    输出 \[false, true, undefined, null, NaN, 0, 1, {}, {}, 'a']
### 答案1  
```  javascript
Array.prototype.uniq = function () {
    return [...new Set(this)]
}
```

### 答案2  
```  javascript
Array.prototype.uniq = function () {
    var res = []
    var flag = true
    for(var i = 0;i<this.length;i++){
        if(res.indexOf(this[i]) == -1){
            if(this[i] != this[i]){
                if(flag){
                   res.push(this[i]);
                   flag = false;
                }
            }else{
                res.push(this[i])
            }
        }
    }
    return res
}
```