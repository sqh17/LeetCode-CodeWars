## 翻转二叉树
  翻转一棵二叉树。
#### 示例1
   输入：

        4
      /   \
      2     7
    / \   / \
    1   3 6   9

    输出：

        4
      /   \
      7     2
    / \   / \
    9   6 3   1

#### 思路

* 标签：DFS
* 找出终止条件：当前节点为空
* 找出返回值：两种方案
  1. 先转换节点左右子树，然后再往下递归，直到为null，返回root （前序遍历）
  2. 先递归，然后转换左右节点，直到为根节点，返回root （后序遍历）
* 某层的执行过程：转换左右子树
* 时间复杂度：O(n)

#### 答案1

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {TreeNode}
 */
var invertTree = function(root) {
  // 遍历到null节点时，不用翻转，直接返回它本身
  if(root == null) return root 
  invertTree(root.right);
  invertTree(root.left);
  let temp = root.left;
  root.left = root.right;
  root.right = temp;

  return root
};
```

#### 答案2

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {TreeNode}
 */
var invertTree = function(root) {
  // 遍历到null节点时，不用翻转，直接返回它本身
  if(root == null) return root 
  let temp = root.left;
  root.left = root.right;
  root.right = temp;

  invertTree(root.right);
  invertTree(root.left);
  
  return root
};
```

#### 思路2

* 标签：BFS
* 根节点先入列，然后出列，出列就 “做事”，交换它的左右子节点（左右子树）。
* 并让左右子节点入列，往后，这些子节点出列，也被翻转。
* 直到队列为空，就遍历完所有的节点，翻转了所有子树。
* 解决问题的代码放在节点出列时。

#### 答案1

```javascript

/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {TreeNode}
 */
var invertTree = function(root) {
  // 遍历到null节点时，不用翻转，直接返回它本身
  if(root == null) return root 
  
  const queue = [root]; // 维护一个队列，初始推入第一层的root
  while(queue.length){
    const cur = queue.shift(); // 出列的节点
    [cur.left, cur.right] = [cur.right, cur.left]; // 交换左右子树

    if (cur.left) {            // 作为下一层节点入列考察
      queue.push(cur.left);
    }
    if (cur.right) {
      queue.push(cur.right);
    }
  }

  return root
};
```