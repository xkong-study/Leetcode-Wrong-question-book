## 首文
首先这个问题我脑子里面没有货了，我唯一能意识到的就是设计一个新的数组用来存储已经使用过的头节点然后还要去重。
我的错误写法只考虑了排序的数组里面不能有重复的 没有考虑不同数组之间是否有重复的，那么就要考虑一个visited数组来存储头节点
重复的关键之处就是：头节点不能在一层里面有一样的
```javaScript
var permuteUnique = function(nums) {
let path = []
let head = []
function dfs(res){
  if(res.length==nums.length){
      path.push([...nums])
      return
  }
  for(let i= 0;i<nums.length;i++){
      if(head.includes(nums[i])) continue
      res.push(nums[i])
      head.push(nums[i])
      dfs(res)
      res.pop()
      head.pop()
  }
}
dfs([])
return path
};
```
## 解决方法：
```javaScript
var permuteUnique = function(nums) {
let path = []
let visited = []
nums.sort((a,b)=>a-b)
function dfs(res){
  if(res.length==nums.length){
    path.push([...res])
    return
  }
  for(let i=0;i<nums.length;i++){
    if(i>0&&nums[i-1]==nums[i]&&!visited.includes(i-1)) continue
    if(visited.includes(i)) continue
    res.push(nums[i])
    visited.push(i)
    dfs(res)
    res.pop()
    visited.pop()
  }
}
dfs([])
return path
};

```
## 主要难点：
- 理解：if(i>0&&nums[i-1]==nums[i]&&!visited.includes(i-1)) continue
这个判断条件起到什么作用：
1.nums[i-1]==nums[i]:数组或者不同数组之间不能有相同的头节点 ---》导致什么问题 数组之间万一有相同的数字那是完全可以的
2.!visited.includes(i-1)：如果能够保证前一个数字没有被用过，那就说明这两个数字不在同一个数组里，那可能就拆成两个数组但是有相同的头节点了

- 理解：if(visited.includes(i)) continue
判断同一个数组里面不能有相同位置的数字


