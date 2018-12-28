## 去掉字符串中的元音字母
    A common way to deal with this situation is to remove all of the vowels from the trolls' comments, neutralizing the threat.
    Your task is to write a function that takes a string and return a new string with all vowels removed.
    请编写一个函数，去掉字符串中的元音字母
#### 示例1
    输入：'This website is for losers LOL!'
    返回：'Ths wbst s fr lsrs LL!'
### 答案1 
```  javascript
/**
 * @param {string} str
 * @return {string}
 */
function disemvowel(str) {
  var arr = Array.from(str);
  for(var i = 0;i<arr.length;i++){
      if(arr[i] == 'a' || arr[i] == 'A' || arr[i] == 'E' || arr[i] == 'e' || arr[i] == 'i' || arr[i] == 'I' || arr[i] == 'o' || arr[i] =='O'|| arr[i] =='U'|| arr[i] =='u'){
          arr[i] = '';
      }
  }
  return arr.join('')
}
```
### 答案2
```  javascript
/**
 * @param {string} str
 * @return {string}
 */
function disemvowel(str) {
  return str.replace(/[aeiou]/gi,'');
}
```
### 答案3
```javascript
function disemvowel(str){
  var vowels = ['a', 'e', 'i', 'o', 'u'];
  return str.split('').filter(function(el) {
    return vowels.indexOf(el.toLowerCase()) == -1;
  }).join('');
}
```
