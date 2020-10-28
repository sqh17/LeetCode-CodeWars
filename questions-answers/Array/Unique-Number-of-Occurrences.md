## 独一无二的出现次数
    给你一个整数数组 arr，请你帮忙统计数组中每个数的出现次数。
    如果每个数的出现次数都是独一无二的，就返回 true；否则返回 false。
#### 示例1
    输入：arr = [1,2,2,1,1,3]
    输出：true
    解释：在该数组中，1 出现了 3 次，2 出现了 2 次，3 只出现了 1 次。没有两个数的出现次数相同。

#### 示例2
    输入：arr = [1,2]
    输出：false

#### 示例3
    输入：arr = [-3,0,1,-3,1,1,1,-3,10,0]
    输出：true   

### 答案1  
```  javascript
/**
 * @param {number[]} arr
 * @return {boolean}
 */
var uniqueOccurrences = function(arr) {
   let res = [...new Set(arr)],obj = {};
    res.forEach(item=>{
        obj[item] = 0
    })
    arr.forEach((item)=>{
        if(res.includes(item)){
            obj[item]++
        }
    })
    if([...new Set(Object.values(obj))].length == res.length){
        return true
    }else{
        return false
    }

};
```

### 答案2  哈希表
```  javascript
/**
 * @param {number[]} arr
 * @return {boolean}
 */
var uniqueOccurrences = function(arr) {
   let res = new Map();
   for(const k of arr){
       if(res.has(k)){
           res.set(k,res.get(k) + 1)
       }else{
           res.set(k,1)
       }
   }
   let times = new Set();
   for(const [key,value] of res){
       times.add(value)
   }
   return times.size === res.size

};
```