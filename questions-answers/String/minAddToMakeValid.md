## minAddToMakeValid
    给定一个由 '(' 和 ')' 括号组成的字符串 S，我们需要添加最少的括号（ '(' 或是 ')'，可以在任何位置），以使得到的括号字符串有效。

    从形式上讲，只有满足下面几点之一，括号字符串才是有效的：

    它是一个空字符串，或者
    它可以被写成 AB （A 与 B 连接）, 其中 A 和 B 都是有效字符串，或者
    它可以被写作 (A)，其中 A 是有效字符串。
    给定一个括号字符串，返回为使结果字符串有效而必须添加的最少括号数。
#### 示例1
    输入："())"
    输出：1
#### 示例2
    输入："((("
    输出：3
#### 示例3
    输入："()"
    输出：0
#### 示例4
    输入："()))(("
    输出：4
```  javascript
/**
 * @param {string} S
 * @return {number}
 */
var minAddToMakeValid = function(S) {
    let pair = 0;
    let res = 0;
    for(let i = 0;i<S.length;i++){
        if(S[i]=='('){
            pair ++;
        }else{
            if(pair >0){
                pair -=1;
            }else{
                res++;
            }
        }
    }
    return res+pair;
};
```
### 答案2
```  javascript
/**
 * @param {string} S
 * @return {number}
 */
var minAddToMakeValid = function(S) {
  if (S.length) {
    return deleRepeat(S);
  } else {
    return 0;
  }
  
  function deleRepeat(S) {
    while (S.length) {
      let temp = S;

      S = S.replace('()', '');

      if (S === temp) {
        return S.length;
      }
    }

    return 0;
  }
};