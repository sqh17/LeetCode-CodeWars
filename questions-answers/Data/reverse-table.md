## 从尾到头打印链表
    输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。
#### 示例1
    输入：head = [1,3,2]
    输出：[2,3,1]
### 思路
  在js中，栈：后进先出 栈方法常用 push/pop，队列：先进先出队列方法常用 push/shift
### 答案  
```  javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {number[]}
 */
var reversePrint = function(head) {
    let res = [];
    let node = head;
    while(node){
        res.push(node.val);
        node = node.next;
    }
    return res.reverse()
};
```