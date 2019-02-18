## 最长公有前缀.
    编写一个函数来查找字符串数组中的最长公共前缀。
    如果不存在公共前缀，返回空字符串 ""。
#### 示例1
    输入: ["flower","flow","flight"]
    输出: "fl"
#### 示例2
    输入: ["dog","racecar","car"]
    输出: ""
    解释: 输入不存在公共前缀。
### 答案 
```  javascript
var longestCommonPrefix = function(strs) {
    var first = strs[0];
    var res = '';
    if(!strs.length) return res;
    for(var i = 0;i<first.length;i++){
        for(var j = 1;j<strs.length;j++){
            if(first[i] != strs[j][i]){
                return res;
            }
        }
        res += first[i]
    }
    return res;
};
```
