## 距离顺序排列矩阵单元格

    给出 R 行 C 列的矩阵，其中的单元格的整数坐标为 (r, c)，满足 0 <= r < R 且 0 <= c < C。
    另外，我们在该矩阵中给出了一个坐标为 (r0, c0) 的单元格。
    返回矩阵中的所有单元格的坐标，并按到 (r0, c0) 的距离从最小到最大的顺序排，其中，两单元格(r1, c1) 和 (r2, c2) 之间的距离是曼哈顿距离，|r1 - r2| + |c1 - c2|。（你可以按任何满足此条件的顺序返回答案。）
#### 示例1
    输入：R = 1, C = 2, r0 = 0, c0 = 0
    输出：[[0,0],[0,1]]
    解释：从 (r0, c0) 到其他单元格的距离为：[0,1]

#### 示例2
    输入：R = 2, C = 2, r0 = 0, c0 = 1
    输出：[[0,1],[0,0],[1,1],[1,0]]
    解释：从 (r0, c0) 到其他单元格的距离为：[0,1,1,2]
    [[0,1],[1,1],[0,0],[1,0]] 也会被视作正确答案。

#### 示例3
    输入：R = 2, C = 3, r0 = 1, c0 = 2
    输出：[[1,2],[0,2],[1,1],[0,1],[1,0],[0,0]]
    解释：从 (r0, c0) 到其他单元格的距离为：[0,1,1,2,2,3]
    其他满足题目要求的答案也会被视为正确，例如 [[1,2],[1,1],[0,2],[1,0],[0,1],[0,0]]。

#### 思路1
    先遍历，将所有情况push到数组中再根据曼哈顿距离进行排序
#### 答案1
    
```  javascript
/**
 * @param {number} R
 * @param {number} C
 * @param {number} r0
 * @param {number} c0
 * @return {number[][]}
 */
var allCellsDistOrder = function(R, C, r0, c0) {
    let res = [];
    for(let i = 0;i<R;i++){
        for(let j = 0;j<C;j++){
            res.push([i,j])
        }
    }
    res.sort((a,b)=>{
        return d(a[0],a[1],r0,c0) - d(b[0],b[1],r0,c0)
    })
    return res
};
var d = (x1, y1, x2, y2) => {
    return Math.abs(x1 - x2) + Math.abs(y1 - y2);
};
```

#### 思路2(桶排序)
    求出矩阵的每个点到 (r0, c0) 的曼哈顿距离
    既然要按照距离大小排，那就把相同距离的坐标放在一个数组里（桶），用一个map管理。
    然后按距离从小到大遍历这些桶，把桶里的坐标，逐个加入结果数组。
#### 答案2
```  javascript
/**
 * @param {number} R
 * @param {number} C
 * @param {number} r0
 * @param {number} c0
 * @return {number[][]}
 */
var allCellsDistOrder = function(R, C, r0, c0) {
    let res = [];
    let hash = {};
    for(let i = 0;i<R;i++){
        for(let j = 0;j<C;j++){
           let dis = d(i,j,r0,c0);
           if(!hash[dis]){
               hash[dis]=[[i,j]]
           }else{
               hash[dis].push([i,j])
           }
        }
    }
    for(let i = 0;i < R+C;i++){
        if(!hash[i]) continue
        for(var c of hash[i]){
            res.push(c)
        }
    }
    return res
};
var d = (x1, y1, x2, y2) => {
    return Math.abs(x1 - x2) + Math.abs(y1 - y2);
};
```