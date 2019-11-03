## shortestWord
    给定一个单词列表，只返回可以使用在键盘同一行的字母打印出来的单词
#### 示例
    输入: ["Hello", "Alaska", "Dad", "Peace"]
    输出: ["Alaska", "Dad"]
### 答案1
```  javascript
/**
 * @param {string[]} words
 * @return {string[]}
 */
var findWords = function(words) {
    let reg = /^([qwertyuiop]+|[asdfghjkl]+|[zxcvbnm]+)$/i;
    let arr = words.filter(item=>{
        return reg.test(item)
    })
    return arr
};
```