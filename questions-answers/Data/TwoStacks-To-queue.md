## 用两个栈实现队列
    用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，deleteHead 操作返回 -1 )
#### 示例1
    输入：
        ["CQueue","appendTail","deleteHead","deleteHead"]
        [[],[3],[],[]]
    输出：[null,null,3,-1]
#### 示例2
    输入：
        ["CQueue","deleteHead","appendTail","appendTail","deleteHead","deleteHead"]
        [[],[],[5],[2],[],[]]
    输出：[null,-1,null,null,5,2]
### 思路
    在js中，栈：后进先出 栈方法常用 push/pop，队列：先进先出队列方法常用 push/shift；
    栈实现不了队列，所以需要采用两个栈弄成一个栈。
    入队过程：
    * 将元素放入 stack1 中。

    出队过程：
    * stack2 不为空：弹出元素
    * stack2 为空：将 stack1 元素依次弹出，放入到 stack2 中（在数据转移过程中，顺序已经从后入先出变成了先入先出）
    
    时间复杂度是 O(N)，空间复杂度是 O(N)。
### 答案  
```  javascript
var CQueue = function() {
    this.stack1 = [];
    this.stack2 = [];
};

/** 
 * @param {number} value
 * @return {void}
 */
CQueue.prototype.appendTail = function(value) {
    this.stack1.push(value)
};

/**
 * @return {number}
 */
CQueue.prototype.deleteHead = function() {
    if(this.stack2.length) return this.stack2.pop();
    while(this.stack1.length){
        this.stack2.push(this.stack1.pop())
    }
    return this.stack2.pop() || -1
};

/**
 * Your CQueue object will be instantiated and called as such:
 * var obj = new CQueue()
 * obj.appendTail(value)
 * var param_2 = obj.deleteHead()
 */
```