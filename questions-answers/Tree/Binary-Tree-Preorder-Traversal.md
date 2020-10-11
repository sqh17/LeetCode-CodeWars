## minAddToMakeValid
    给定一个二叉树，返回它的 前序 遍历。
#### 示例1
    输入: [1,null,2,3] 
    输出：[1,2,3]
#### 进阶
    递归算法很简单，你可以通过迭代算法完成吗？
#### 思路
  * 前序遍历
    对于二叉树中的任意一个节点，先打印该节点，然后是它的左子树，最后右子树
  * 中序遍历
    对于二叉树中的任意一个节点，先打印它的左子树，然后是该节点，最后右子树
  * 后序遍历
    对于二叉树中的任意一个节点，先打印它的左子树，然后是右子树，最后该节点
#### 答案1
```  javascript
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
 * @return {number[]}
 */
var preorderTraversal = function(root) {
  let list = [];
  let foo = (root) => {
    if(root) {
      list.push(root.val); // 先打印该节点
      foo(root.left); // 遍历左子树
      foo(root.right); // 遍历右子树
    }
  }
  foo(root);
  return list
};
```
#### 进阶-思路
利用栈来记录遍历的过程，实际上，递归就使用了调用栈，所以这里我们可以使用栈来模拟递归的过程

* 首先根入栈
* 将根节点出栈，将根节点值放入结果数组中
* 然后遍历左子树、右子树，因为栈是先入后出，所以，我们先右子树入栈，然后左子树入栈
* 继续出栈（左子树被出栈）…….

依次循环出栈遍历入栈，直到栈为空，遍历完成

#### 答案2

```  javascript
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
 * @return {number[]}
 */
var preorderTraversal = function(root) {
  let list = [],stack = [];
  if(root) stack.push(root);// 当根节点不为空的时候，将根节点入栈
  while(stack.length > 0){
    
    const curNode = stack.pop();
    list.push(curNode.val); // 第一步的时候，先访问的是根节点
    // 我们先打印左子树，然后右子树
    // 所以先加入栈的是右子树，然后左子树
    if(curNode.right !== null) {
      stack.push(curNode.right)
    }
    if(curNode.left !== null) {
      stack.push(curNode.left)
    }
  }
  return list;
};
```