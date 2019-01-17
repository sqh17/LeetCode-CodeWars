## humanReadable
  写一个函数将秒数转化成hh:mm:ss的形式
#### 
    humanReadable(450) => 00:07:30
    humanReadable(45022) => 12:30:22
### 答案1
```  javascript
function humanReadable(seconds) {
    // TODO
    var hour,minutes,seconds1;
    if(seconds < 60){
        seconds1 = seconds>10?seconds:`0${seconds}`
        return `00:00:${seconds1}`
    } else{
        minutes = Math.floor(seconds / 60);
        seconds1 = seconds % 60;
        if(minutes >= 60){
            hour = Math.floor(minutes / 60);
            minutes = minutes % 60;
        } else{
          hour = 0;  
          minutes = minutes % 60;
        }
        hour = hour>10?hour:`0${hour}`;
        minutes = minutes>10?minutes:`0${minutes}`;
        seconds1 = seconds1>10?seconds1:`0${seconds1}`
        return `${hour}:${minutes}:${seconds1}`
    }
}
```
### 答案2
```javascript
function humanReadable(seconds) {
    // TODO
    var hour = parseInt(seconds / 3600);
    var minutes = parseInt(seconds / 60) % 60;   // %60代表可能会出现大于60min的情况
    var seconds1 = seconds % 60;
    var pad = function (val){
        return val>10?val:`0${val}`
    }
    console.log(`${pad(hour)}:${pad(minutes)}:${pad(seconds1)}`)
    return `${pad(hour)}:${pad(minutes)}:${pad(seconds1)}`

}
```
