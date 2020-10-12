## 第 N 个泰波那契数 XXX
    泰波那契序列 Tn 定义如下： 
    T0 = 0, T1 = 1, T2 = 1, 且在 n >= 0 的条件下 Tn+3 = Tn + Tn+1 + Tn+2

    给你整数 n，请返回第 n 个泰波那契数 Tn 的值。
    
#### 示例
    输入：n = 4
    输出：4
    解释：
    T_3 = 0 + 1 + 1 = 2
    T_4 = 1 + 1 + 2 = 4
#### 思路
    没解决，看解题，总结如下：
    1. 普通递归会爆栈，不使用
    2. 递归+缓存
    3. 循环
    4. 动态规划
### 答案1 普通递归会爆栈，不使用
```  javascript
/**
 * @param {number} n
 * @return {number}
 */
var tribonacci = function(n) {
  if(n == 0) return 0;
  if(n == 1) return 1;
  if(n == 2) return 1;
  return tribonacci(n - 1) + tribonacci(n - 2) + tribonacci(n - 3)
};
```
### 答案2
```  javascript
/**
 * @param {number} n
 * @return {number}
 */
let cache = {};
var tribonacci = function(n) {
  if (n === 0) return 0
  if (n === 1) return 1
  if (n === 2) return 1
  if(cache[n]) return cache[n];
  let res = tribonacci(n-1) + tribonacci(n-2) + tribonacci(n-3) 
  cache[n] = res
  return res
};
```
### 答案3
```  javascript
/**
 * @param {number} n
 * @return {number}
 */
var tribonacci = function(n) {
  if (n === 0) return 0
  if (n === 1) return 1
  if (n === 2) return 1
  let x = 0
  let y = 1
  let sum = 1
  for(let i =2; i<n; i++) {
      let t = x
      x = y
      y =  sum

      sum = t + y + x
  }
  return sum
};
```
### 答案4
```  javascript
/**
 * @param {number} n
 * @return {number}
 */
var tribonacci = function(n) {
  const ans = [0, 1, 1];
  for (let i = 3; i <= n; i++) {
    ans[i] = ans[i - 3] + ans[i - 2] + ans[i - 1];
  }
  return ans[n];
};
```

