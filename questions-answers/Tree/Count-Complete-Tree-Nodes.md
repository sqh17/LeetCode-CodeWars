##  完全二叉树的节点个数
    给出一个完全二叉树，求出该树的节点个数。
    说明：
      完全二叉树的定义如下：在完全二叉树中，除了最底层节点可能没填满外，其余每层节点数都达到最大值，并且最下面一层的节点都集中在该层最左边的若干位置。若最底层为第 h 层，则该层包含 1~ 2^h 个节点。
#### 示例1

    输入: 
           1
          / \
         2   3
        / \ /
       4  5 6

    输出: 6
#### 思考
  完全二叉树
  1. 如果树为空，则直接返回错
  2. 如果树不为空：层序遍历二叉树
    2. 如果一个结点，左孩子为空，右孩子不为空，则该树一定不是完全二叉树；
    3. 如果一个结点，左孩子不为空，右孩子为空；或者左右孩子都为空；则该节点之后的队列中的结点都为叶子节点；该树才是完全二叉树，否则就不是完全二叉树；
#### 思路1
  ![完全二叉树的方式](https://github.com/sqh17/LeetCode-CodeWars/tree/master/questions-answers/images/Count-Complete-Tree-Nodes.png)

  * 对于一个完全二叉树：
    * 它的所有子树都是完全二叉树
    * 有的子树是 perfect binary tree
    * perfect binary tree 的节点个数很好计算：2^h-1，h为高度
    * 如果不是 perfect binary tree，那就是规模小一点的完全二叉树，递归处理。
    * 都判断一下它是否是满二叉树  — 左侧的高度 == 右侧的高度。

#### 答案1
```  javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number}
 */
var countNodes = function (root) {
  if(root === null) return 0;
  let lH, rH = 0; // 记录个数
  let lNode = root;
  let rNode = root; 

  while(lNode){ // 遍历左子树
    lH++;
    lNode = lNode.left;
  }

  while(rNode){ // 遍历右子树
    rH++;
    rNode = rNode.left;
  }

  // 当两方个数一样时，代表是满二叉树
  if(lH === rH) return 2 ** lH - 1;

  return 1 + countNodes(root.left) + countNodes(root.right);
}
```


##### 思路2
  位运算？？？？
