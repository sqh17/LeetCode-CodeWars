## 整数转罗马数字
    罗马数字包含以下七种字符： I， V， X， L，C，D 和 M。

    字符          数值
    I             1
    V             5
    X             10
    L             50
    C             100
    D             500
    M             1000
    例如， 罗马数字 2 写做 II ，即为两个并列的 1。12 写做 XII ，即为 X + II 。 27 写做  XXVII, 即为 XX + V + II 。

    通常情况下，罗马数字中小的数字在大的数字的右边。但也存在特例，例如 4 不写做 IIII，而是 IV。数字 1 在数字 5 的左边，所表示的数等于大数 5 减小数 1 得到的数值 4 。同样地，数字 9 表示为 IX。这个特殊的规则只适用于以下六种情况：

        I 可以放在 V (5) 和 X (10) 的左边，来表示 4 和 9。
        X 可以放在 L (50) 和 C (100) 的左边，来表示 40 和 90。 
        C 可以放在 D (500) 和 M (1000) 的左边，来表示 400 和 900。
    给定一个整数，将其转为罗马数字。输入确保在 1 到 3999 的范围内。
#### 示例1
    输入: 3
    输出: "III"
#### 示例2
    输入: 4
    输出: "IV"
#### 示例3
    输入: 58
    输出: "LVIII"
    解释: L = 50, V = 5, III = 3.
#### 示例4
    输入: 1994
    输出: "MCMXCIV"
    解释: M = 1000, CM = 900, XC = 90, IV = 4.
#### 思路1
    贪心算法
    从问题的某一初始解出发：

        while (朝给定总目标前进一步)
        {
            利用可行的决策，求出可行解的一个解元素。
        }

    由所有解元素组合成问题的一个可行解；
#### 答案1
```  javascript
/**
 * @param {number} num
 * @return {string}
 */
var intToRoman = function(nums) {
    let keys = [1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1];
    let values = ['M', 'CM', 'D', 'CD', 'C', 'XC', 'L', 'XL', 'X', 'IX', 'V', 'IV', 'I'];
    let res = '';
    for(let i = 0;i<keys.length;i++){
        while(nums >= keys[i]){
            nums -= keys[i];
            res += values[i]
        }
    }
    return res
}

```
#### 思路2
    暴力
    num => num/1000 + (num%1000)/100 +(num%100)/10 + num%10

    
    个位【1-9】：I、II、III、IV、V、VI、VII、VIII、IX （对应阿拉伯数字 X%10）
    十位【1-9】：X、XX、XXX、XL、L、LX、LXX、LXXX、XC （对应阿拉伯数字 (X%100)/10）
    百位【1-9】：C、CC、CCC、CD、D、DC、DCC、DCCC、CM （对应阿拉伯数字 (X%1000)/100）
    千位【1-9】：M、MM、MMM （对应阿拉伯数字 X/1000）
### 答案2
```  javascript
/**
 * @param {number} num
 * @return {string}
 */
var intToRoman = function(num) {
    var Q = ["", "M", "MM", "MMM"];
    var B = ["", "C", "CC", "CCC", "CD", "D", "DC", "DCC", "DCCC", "CM"];
    var S = ["", "X", "XX", "XXX", "XL", "L", "LX", "LXX", "LXXX", "XC"];
    var G = ["", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX"];
    return Q[Math.floor(num/1000)] + B[Math.floor((num%1000)/100)] + S[Math.floor((num%100)/10)] + G[num%10];
};
```