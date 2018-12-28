## 翻转字符串
  给定一个字符串，找到它的第一个不重复的字符，并返回它的索引。如果不存在，则返回 -1。
#### 示例1
    s = "leetcode"
    返回 0.
#### 示例2
    s = "loveleetcode",
    返回 2.
### 思路
    1 双重循环，如果有相等，则count+1，同时count的个数大于1的话，直接跳出内循环
    2 内循环外，如果count == 1，则返回索引值
    3 外循环，跳出break的，就直接返回-1
### 答案1  
```  javascript
/**
 * @param {string} s
 * @return {number}
 */
var firstUniqChar = function (s) {
    var count = 0;
    for (var i = 0; i < s.length; i++) {
        for (var j = 0; j < s.length; j++) {
            if (s[i] == s[j]) {
                count++
            }
            if (count > 1) break;
        }
        if (count == 1) return i
        count = 0
    }
    return -1
};
```
### 答案2(不全符合题干要求)  
```  javascript
/**
 * @param {string} s
 * @return {number}
 */
var firstUniqChar = function (s) {
    if(s.length == 0) return -1;
    for(var i = 0;i<s.length;i++){
        var first = s.indexOf(s.chartAt(i));
        var last = s.lastIndexOf(s.chartAr(i));
        if(first == last){
            return first
        }
    }
};
```