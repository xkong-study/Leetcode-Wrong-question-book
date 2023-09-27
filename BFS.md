# Understanding BFS in Binary Trees

## 1. Objective

The primary goal of the provided code is to return a two-dimensional array where each internal array represents a level of the tree, traversed from top to bottom.

## 2. Utilizing a Queue

In Breadth-First Search (BFS) of trees, a common data structure employed is a queue. With the help of a queue, we can ensure nodes are processed in the order they are entered into the queue.

### 2.1 Code Breakdown

- **res**: This is used to store the final result.
- **queue**: This keeps track of nodes at each level.

Each iteration of the outer loop processes one level of the tree:
1. A new array is initialized at the beginning of each loop to store nodes of the current level.
2. The loop runs for the number of nodes at the current level (determined by the current length of the queue).
3. Nodes of the current level are dequeued, and their values are stored in the array.
4. Child nodes (if present) of the dequeued node are enqueued. This ensures that nodes of the next level are processed in the subsequent loop.
  
After processing all nodes of the current level, the array is added to `res`.

Once all levels are processed, `res` is returned as the final result.

### 2.2 Code Snippet

```javascript
var levelOrder = function(root) {
    let res = [];
    let queue = [];
    queue.push(root);
    if(root == null) return res;
    while(queue.length != 0) {
        let length = queue.length;
        let arr = [];
        for(let i = 0; i < length; i++) {
            let node = queue.shift();
            arr.push(node.val);
            node.left && queue.push(node.left);
            node.right && queue.push(node.right);
        }
        res.push(arr);
    }
    return res;
};
```

## 2.3 Knowledge comprehension --- why choose queue
## 栈和队列的区别

栈和队列都是线性数据结构，但它们在处理元素的方式上存在明显的不同。以下是栈和队列之间的主要区别：

### 基本概念:
- **栈 (Stack)**: 是一种后进先出 (LIFO, Last In First Out) 的数据结构，这意味着最后一个添加到栈中的元素会是第一个被移除的。
- **队列 (Queue)**: 是一种先进先出 (FIFO, First In First Out) 的数据结构，这意味着最先添加到队列的元素会是第一个被移除的。

### 主要操作:
#### 栈:
- `push`: 添加元素到栈顶。
- `pop`: 从栈顶移除元素。

> **注意**: 在JavaScript的数组中，`push()`方法可以用来添加元素到数组的末尾，而`pop()`方法可以从数组末尾移除元素。因此，可以使用这两个方法来实现栈的操作。


## 2.4我有个问题queue和stack的定义方式都是[],js是如何分清的
在 JavaScript 中，没有为栈（Stack）和队列（Queue）提供独立的内置数据结构。它们都使用数组来实现。因此，数组本身并不知道它是用作栈还是用作队列。实际上，JavaScript 中的数组具有足够的灵活性，可以同时作为栈和队列使用。

区分它们的关键是你如何操作这个数组：

栈 (Stack):

用 push 方法来添加元素到数组的末尾
用 pop 方法从数组的末尾移除元素
这样的操作确保了后进先出 (LIFO) 的行为。
队列 (Queue):

用 push 方法来添加元素到数组的末尾
用 shift 方法从数组的开头移除元素
这样的操作确保了先进先出 (FIFO) 的行为。
因此，区分栈和队列并不是基于数据结构本身，而是基于你如何操作这个数据结构。你可以有一个数组，既用作栈又用作队列，只是要确保不在同一个操作序列中混合使用栈和队列的操作方式。


