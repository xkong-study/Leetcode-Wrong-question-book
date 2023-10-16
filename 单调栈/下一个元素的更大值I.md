我的错误写法
```javaScript
var nextGreaterElement = function(nums1, nums2) {
    let res = new Array(nums1.length).fill(-1);
    let stack = [];
    for (let i = 0; i < nums1.length; i++) {
        while (nums1[stack[stack.length - 1]] < nums2[i]) {
            let j = stack.pop();
            res[j] = nums2[j];
        }
        stack.push(i);
    }
    return res;
};
```
正确写法
```javaScript
var nextGreaterElement = function(nums1, nums2) {
    let res = new Array(nums1.length).fill(-1);
    let stack = [];
    for (let i = 0; i < nums2.length; i++) {
        while (stack.length > 0 && nums2[i] > nums2[stack[stack.length - 1]]) {
            let j = stack.pop();
            res[nums1.indexOf(nums2[j])] = nums2[i];
        }
        stack.push(i);
    }
    return res;
};

```
我的错误原因：

我的错误主要在于遍历的数组选择和单调栈的使用方式。我没有理解遍历的数组选择是什么，以及单调栈的使用方法。
做题逻辑：
1.stack一定存的都是一个数组的索引。

2.res一定是用来存答案的

3.所以就是遍历的数组是哪一个有的时候不好判断

1） **目标**：看题目主要关注哪个数组的元素，通常就遍历这个数组。

2） **完整性**：如果一个数组包含另一个数组的所有元素，通常遍历更完整的那个。



