我写的正确答案
```javaScript
let res = new Array(nums.length).fill(-1)
let stack = []
const arrCopy = JSON.parse(JSON.stringify(nums));
arrCopy.push(...nums.slice(0,nums.length))
for(let i=0;i<=arrCopy.length;i++){
    while(stack.length && arrCopy[i]>arrCopy[stack[stack.length-1]]){
        let j = stack.pop()
        res[j] = arrCopy[i]
    }
    stack.push(i)
 }
const array= res.splice(0,nums.length)
return array;
};
```
看看有没有代码优化的方法！

用数学方法优化 i%n

```javaScript
var nextGreaterElements = function(nums) {
    const n = nums.length;
    const ret = new Array(n).fill(-1);
    const stk = [];
    for (let i = 0; i < n * 2 - 1; i++) {
        while (stk.length && nums[stk[stk.length - 1]] < nums[i % n]) {
            ret[stk[stk.length - 1]] = nums[i % n];
            stk.pop();
        }
        stk.push(i % n);
    }
    return ret;
};

作者：力扣官方题解
链接：https://leetcode.cn/problems/next-greater-element-ii/solutions/637573/xia-yi-ge-geng-da-yuan-su-ii-by-leetcode-bwam/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```
