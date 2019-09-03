## shortestWord
    给定一个字符串，逐个翻转字符串中的每个单词。
#### 示例1
    输入: "the sky is blue"
    输出: "blue is sky the"
    解释: 无空格字符构成一个单词。
#### 示例2
    输入: "  hello world!  "
    输出: "world! hello"
    解释: 输入字符串可以在前面或者后面包含多余的空格，但是反转后的字符不能包括。
#### 示例3
    输入: "a good   example"
    输出: "example good a"
    解释: 如果两个单词间有多余的空格，将反转后单词间的空格减少到只含一个。

### 答案
```  javascript
/**
 * @param {string} s
 * @return {string}
 */
var reverseWords = function(s) {
    s = s.replace(/(^\s*)|(\s*$)/g, "").replace(/(\s{2,})/g,' ') //去掉首尾空格和单词之间的多个空格为一个空格
    return s.split(' ').reverse().join(' ')
};