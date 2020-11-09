## 最接近原点的 K 个点
    我们有一个由平面上的点组成的列表 points。需要从中找出 K 个距离原点 (0, 0) 最近的点。
    （这里，平面上两点之间的距离是欧几里德距离。）
    你可以按任何顺序返回答案。除了点坐标的顺序之外，答案确保是唯一的。
#### 示例1
    示例 1：

    输入：points = [[1,3],[-2,2]], K = 1
    输出：[[-2,2]]

    解释： 
    (1, 3) 和原点之间的距离为 sqrt(10)，
    (-2, 2) 和原点之间的距离为 sqrt(8)，
    由于 sqrt(8) < sqrt(10)，(-2, 2) 离原点更近。
    我们只需要距离原点最近的 K = 1 个点，所以答案就是 [[-2,2]]。

#### 示例2
    输入：points = [[3,3],[5,-1],[-2,4]], K = 2
    输出：[[3,3],[-2,4]]
    （答案 [[-2,4],[3,3]] 也会被接受。）
#### 思路
    欧几里德距离 算法是 Math.sqrt((x2 - x1)^2 + (y2 - y1)^2)
    创建一个数组对象，循环数组，对每一个对象的平方和进行排序，之后再利用K进行循环,K代表的是个数
#### 答案(自己写)
```  javascript
/**
 * @param {number[][]} points
 * @param {number} K
 * @return {number[][]}
 */
var kClosest = function(points, K) {
  if(points.length == 1) return points
  let arr = [];
  let res = [];
  for(let i = 0;i<points.length;i++){
      let obj = {};
      obj['arr'] = points[i];
      obj['product'] = points[i][0] ** 2 + points[i][1] ** 2;
      arr.push(obj)
  }
  arr.sort((a,b)=>{
    return a.product - b.product
  });
  for(let i = 0;i<K;i++){
    res.push(arr[i]['arr'])
  }
  return res
};
```
#### 思路2 （快排）
下面表述的，用于比较大小的“元素”，都指的是坐标到原点的距离。

用快排的思路，将小的排在前面，选一个主元元素作为pivot，将数组分为两部分：

* 小于等于 pivot 的元素
* 大于 pivot 的元素
我们把数组最左项作为 pivot，安排两个首尾指针：

* 如果左指针元素 <= pivot，是ok的，左指针右移，看下一个。
* 如果右指针元素 > pivot，也是ok的，右指针左移，看下一个。
* 如果左指针元素 > pivot，右指针元素 <= pivot，则小的应该到前面来，它们交换位置，指针同时收缩1，看下一个元素。

直到双指针交错，循环结束，此时左边都是小于等于 pivot 的，右边都是大于 pivot 的。

别忘了：将 pivot 元素与当前右指针元素交换，交换后，pivot 元素来到右指针的位置，它的左边都是小于等于它的，它的位置，是继续分治的位置。

然后来到判断：

* 如果右指针索引 right == K，则说明 right 的左边有 K 个元素，已经排好了。
* 如果 right < K，说明 right 左边不足 K 个元素，说明右边的序列有些小的没排前面来，继续递归排。
* 如果 right > K，说明 right 左边多于 K 个元素，说明左边的序列还没排好，继续递归排。

#### 答案2
```  javascript
/**
 * @param {number[][]} points
 * @param {number} K
 * @return {number[][]}
 */
var kClosest = function (points, K) {
  if (points.length <= K) {
    return points;
  }
  quickSelect(points, 0, points.length - 1, K); // 范围是整个数组
  console.log(points.slice(0, K))
  return points.slice(0, K);  // 排完后，取前K个
};
function quickSelect(points, start, end, K) {
  const p = d(points[start]); // pivot
  let l = start, r = end;
  while (l <= r) { 	     // 左右两个指针
    if (d(points[l]) <= p) { // 左指针指向的元素比pivot小，没毛病，看下一个，指针右移
      l++;
      continue;
    }
    if (d(points[r]) > p) { // 右指针指向的元素比pivot大，没毛病，看下一个，指针左移
      r--;
      continue;
    }
    // 左指针指向的元素比pivot大，右指针指向的元素比pivot小，交换左右指针指向的元素
    [points[l], points[r]] = [points[r], points[l]];
    l++;
    r--;        // 指针同时收缩1
  }
  [points[start], points[r]] = [points[r], points[start]]; // 交换pivot元素和右指针指向的元素
  if (r == K) { // 排好了
    return;
  } else if (r < K) { // 左边还不够K个，则[r+1:end]要继续排
    quickSelect(points, r + 1, end, K);
  } else { // 左边大于K个，则对左边继续排
    quickSelect(points, start, r - 1, K);
  }
}

function d(point) {  // 求point到原点的距离
  return point[0] * point[0] + point[1] * point[1];
}
```