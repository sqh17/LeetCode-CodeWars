## 无重复字符的最长子串
    给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。
#### 示例1
    输入: s = "abcabcbb"
    输出: 3 
    解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。

#### 示例2
    输入: s = "bbbbb"
    输出: 1
    解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。

#### 示例3
    输入: s = "pwwkew"
    输出: 3
    解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。

#### 示例4
    输入: s = ""
    输出: 0

#### 思路1
* 使用一个数组来维护滑动窗口
* 遍历字符串，判断字符是否在滑动窗口数组里
    * 不在则 push 进数组
    * 在则删除滑动窗口数组里相同字符及相同字符前的字符，然后将当前字符 push 进数组
    * 然后将 max 更新为当前最长子串的长度
* 遍历完，返回 max 即可
#### 答案1
```  javascript
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
    let arr = [];
    let max = 0;
    for(let i = 0;i<s.length;i++){
        let index = s.indexOf(s[i]);
        if(index !== -1){
            arr.splice(0,index + 1);
        }
        arr.push(s.charAt(i));
        max = Math.max(arr.length,max)
    }
    
    return max
};
```

#### 思路2
    双指针，使用下标来维护滑动窗口
#### 答案2
```  javascript
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
    let index = 0, max = 0
    for(let i = 0, j = 0;j<s.length;j++){
        index = s.subString(i,j).indexOf(s[j]);
        if(index !== -1){
            i = i + index + 1;
        }
        max = Math.max(max, j - i +1);
        
    }
    
    return max
};
```
### 答案3
```javascript
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
    let map = new Map(), max = 0
    for(let i = 0, j = 0;j<s.length;j++){
        
        if(map.has(s[j])){
            i = Math.max(map.get(s[j]) + 1,i)
        }
        max = Math.max(max, j - i +1);
        map.set(s[j],j)
    }
    
    return max
};
```