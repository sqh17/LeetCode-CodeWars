## First non-repeating character
    Write a function named first_non_repeating_letter that takes a string input, and returns the first character that is not repeated anywhere in the string.
    请编写一个函数，找出一个字符中第一个不重复的值，如果全都有重复的，且返回''，看例子
#### 示例1
    输入：'a'
    返回：'a'
#### 示例2
    输入：'stress'
    返回：'t'
#### 示例3
    输入：'moonmen'
    返回：'e'
#### 示例4
    输入：'sTreSS'
    返回：'T'
### 答案1 
```  javascript
function firstNonRepeatingLetter(s) {
  // Add your code here
  var count = 0;
    for (var i = 0; i < s.length; i++) {
        for (var j = 0; j < s.length; j++) {
            if (s[i].toLowerCase() == s[j].toLowerCase()) {
                count++
            }
            if (count > 1) break;
        }
        if (count == 1) return s[i]
        count = 0
    }
  return ''
}
```
### 答案2
```  javascript
function firstNonRepeatingLetter(s) {
  for(var i in s) {
    if(s.match(new RegExp(s[i],"gi")).length === 1) {
      return s[i];
    }
  }
  return '';
}
```
### 答案3
```  javascript
function firstNonRepeatingLetter(s) {
  var t=s.toLowerCase();
  for (var x=0;x<t.length;x++)
    if(t.indexOf(t[x]) === t.lastIndexOf(t[x]))
      return s[x];
  return "";
}
```
