## 对称二叉树
  给定一个二叉树，检查它是否是镜像对称的。翻转一棵二叉树。
  进阶：
  你可以运用递归和迭代两种方法解决这个问题吗？
#### 示例1
   输入： [1,2,2,3,4,4,3]

         1
        / \
        2   2
      / \ / \
      3  4 4  3

    输出：true

#### 示例2
   输入： [1,2,2,null,3,null,3]

         1
        / \
        2   2
        \   \
        3    3

    输出：false


#### 思路1-递归
根的左右子树是镜像对称的,依次往下也是对称的
* 只需要比较
  * 左右子树的根节点值是否相等
  * 左右子树是否镜像对称
* 边界情况
  * 左右子树都为 null 时，返回 true
  * 左右子树有一个 null 时，返回 false

#### 答案1-递归

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {boolean}
 */
var isSymmetric = function(root) {
  if(!root) return true
  var isEqual = function(left, right) {
      if(!left && !right) return true
      if(!left || !right) return false
      return left.val === right.val && isEqual(left.left, right.right) && isEqual(left.right, right.left)
  }
  return isEqual(root.left, root.right)
};
```

#### 思路2-迭代
利用栈来记录比较的过程，实际上，递归就使用了调用栈，所以这里我们可以使用栈来模拟递归的过程

- 首先根的左右子树入栈
- 将左右子树出栈，比较两个数是否互为镜像
- 如果左右子树的根节点值相等，则将左子树的 left 、右子树的 right 、左子树的 right 、右子树的 left 依次入栈
- 继续出栈（一次出栈两个进行比较）
依次循环出栈入栈，直到栈为空

#### 答案2-迭代

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {boolean}
 */
var isSymmetric = function(root) {
  if(!root) return true
  let stack = [root.left, root.right]
  while(stack.length) {
      let right = stack.pop()
      let left = stack.pop()
      if(left && right) {
          if(left.val !== right.val) return false
          stack.push(left.left)
          stack.push(right.right)
          stack.push(left.right)
          stack.push(right.left)
      } else if(left || right) {
          return false
      }
  }
  return true
};
```