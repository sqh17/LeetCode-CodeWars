## 实现 strStr()
    实现 strStr() 函数。
    给定一个 haystack 字符串和一个 needle 字符串，在 haystack 字符串中找出 needle 字符串出现的第一个位置 (从0开始)。如果不存在，则返回  -1。

#### 示例1
    输入: haystack = "hello", needle = "ll"
    输出: 2
#### 示例2
    输入: haystack = "aaaaa", needle = "bba"
    输出: -1
### 答案1
```  javascript
/**
 * @param {string} haystack
 * @param {string} needle
 * @return {number}
 */
var strStr = function(haystack, needle) {
    return haystack.indexOf(needle)
}
```
### 答案2
```  javascript
var strStr = function (haystack, needle) {
    if (needle === "") return 0
    for (var i = 0; i < haystack.length; i++) {
        if (haystack[i] === needle[0]) {
            if (haystack.substring(i, i + needle.length) === needle) return i;
        }
    }
    return -1
};
```
### 答案3
```javascript
```