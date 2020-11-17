## 两数相加
    给出两个 非空 的链表用来表示两个非负的整数。其中，它们各自的位数是按照 逆序 的方式存储的，并且它们的每个节点只能存储 一位 数字。
    如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。
    您可以假设除了数字 0 之外，这两个数都不会以 0 开头。
#### 示例
    输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
    输出：7 -> 0 -> 8
    原因：342 + 465 = 807
#### 思路
    1. 从低位算起
    2. 将这俩的和作为输出结果的最低位
    3. 进位，设置一个变量作为进位判断，当大于10时进位为1，否则为0
    4. 
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
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var addTwoNumbers = function(l1, l2) {
    let addOne = 0;
    let sum = new ListNode('0'); // 创建一个头链表用于保存结果
    let head = sum; // 保存头链表的位置用于最后的链表返回
    while(l1 || l2 || addOne){
        let val1 = l1 !== null ? l1.val : 0 // 要考虑位数不一致的情况，若l1有值，l2没值，则设置l2为0
        let val2 = l2 !== null ? l2.val : 0
        let r1 = val1 + val2 + addOne;
        addOne = r1 >= 10 ? 1 : 0;
        sum.next = new ListNode(r1 % 10);//sum的下一个节点
        sum = sum.next; //sum指向下一个节点

        if (l1) l1 = l1.next // l1指向下一个节点，以便计算第二个节点的值
        if (l2) l2 = l2.next //l2指向下一个节点，以便计算第二个节点的值
        
    }
    return head.next //返回计算结果，之所以用head.next是因为head中保存的第一个节点是刚开始定义的“0”
};
```