## VectorClass.
    Create a Vector object that supports addition, subtraction, dot products, and norms. So, for example:
#### 示例1
    var a = new Vector([1, 2, 3]);
    var b = new Vector([3, 4, 5]);
    var c = new Vector([5, 6, 7, 8]);

    a.add(b);      // should return a new Vector([4, 6, 8])
    a.subtract(b); // should return a new Vector([-2, -2, -2])
    a.dot(b);      // should return 1*3 + 2*4 + 3*5 = 26
    a.norm();      // should return sqrt(1^2 + 2^2 + 3^2) = sqrt(14)
    a.add(c);      // throws an error

### 答案(不是自己写的)
```  javascript
var Vector = function (components) {
  this.x = components;
};
Vector.prototype.add = function (b) {
  var a = this.x
  console.log('b.x',b)
  b = b.x;
  
  if (a.length !== b.length) throw new TypeError("Vectors have different length");
  return new Vector(a.map(function (x, i) { return x + b[i]; }));
}
Vector.prototype.subtract = function (b) {
  var a = this.x;
  b = b.x;
  if (a.length !== b.length) throw new TypeError("Vectors have different length");
  return new Vector(a.map(function (x, i) { return x - b[i]; }));
}
Vector.prototype.dot = function (b) {
  var a = this.x;
  b = b.x;
  if (a.length !== b.length) throw new TypeError("Vectors have different length");
  return a.reduce(function (s, x, i) { return s + x * b[i]; }, 0);
}
Vector.prototype.equals = function (b) {
  var a = this.x;
  b = b.x;
  if (a.length !== b.length) return false;
  return a.every(function (x, i) { return x === b[i]; });
}
Vector.prototype.norm = function () {
  var a = this.x;
  return Math.sqrt(a.reduce(function (s, x) { return s + x * x }, 0));
}
Vector.prototype.toString = function () {
  return '(' + this.x.join(',') + ')';
}
```

