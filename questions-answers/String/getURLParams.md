## getURLParams
    获取url的参数
    1. 指定参数名称，返回该参数的值 或者 空字符串
    2. 不指定参数名称，返回全部的参数对象 或者 {}
    3. 如果存在多个同名参数，则返回数组
### 答案1
```  javascript
var str = 'http://www.baidu.com?key=1&key=2&test=3#hashed'
function getURLParams (url, skey) {
  var params = url.split('#')[0].split('?')[1]
  var arr = params.split('&')
  var obj = {}
  var newArr = []
  if (skey) {
    arr.forEach(item => {
      if (item.indexOf(skey) != -1) {
        newArr.push(item.substring(item.indexOf('=') + 1, item.length))
      }
    })
    if (newArr.length == 1) {
      return newArr[0]
    } else if (newArr.length == 0) {
      return ''
    } else {
      return newArr
    }
  } else {
    if (arr.length == 0) return {}
    arr.forEach((item) => {
      var index = item.split('=')
      if (!(index[0] in obj)) {
        obj[index[0]] = []
      }
      obj[index[0]].push(index[1])
    })
    return obj
  }
}
```
### 答案3
```javascript
function getUrlParam(sUrl,sKey){
    var result = {};
    sUrl.replace(/\??(\w+)=(\w+)&?/g,function(a,k,v){
        if(result[k] !== void 0){
            var t = result[k];
            result[k] = [].concat(t,v);
        }else{
            result[k] = v;
        }
    });
    if(sKey === void 0){
        return result;
    }else{
        return result[sKey] || '';
    }
}
```