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
