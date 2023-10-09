有时候可能考正则运算
**1. 修改数组：**

- `push(item1, item2, ...)`：向数组末尾添加一个或多个元素，返回新数组的长度。
- `pop()`：从数组末尾删除最后一个元素，返回被删除的元素。
- `unshift(item1, item2, ...)`：向数组开头添加一个或多个元素，返回新数组的长度。
- `shift()`：从数组开头删除第一个元素，返回被删除的元素。
- `splice(startIndex, deleteCount, item1, item2, ...)`：从指定位置开始删除/替换元素，返回删除的元素组成的数组。
- `reverse()`：颠倒数组的顺序，原地修改数组。
- `sort(compareFunction)`：对数组元素进行排序，原地修改数组。

**2. 迭代数组：**

- `forEach(callback)`：遍历数组的每个元素并执行回调函数，不创建新数组。
- `map(callback)`：对数组的每个元素执行回调函数，返回新数组，不修改原数组。
- `filter(callback)`：根据回调函数的条件筛选数组元素，返回新数组。
- `reduce(callback, initialValue)`：将数组元素累加或组合成一个值，返回最终结果。
- `reduceRight(callback, initialValue)`：从数组的右侧开始执行 reduce，返回最终结果。

**3. 查找元素：**

- `indexOf(item)`：查找数组中第一个匹配元素的索引，如果不存在返回 -1。
- `lastIndexOf(item)`：查找数组中最后一个匹配元素的索引，如果不存在返回 -1。
- `includes(item)`：检查数组是否包含指定元素，返回布尔值。
- `some(callback)`：检查数组是否至少有一个元素满足条件，返回布尔值。
- `every(callback)`：检查数组是否所有元素都满足条件，返回布尔值。

**4. 转换和连接：**

- `concat(array2, array3, ...)`：将多个数组合并成一个新数组，不修改原数组。
- `join(separator)`：将数组元素拼接成一个字符串，可指定分隔符。
- `toString()`：将数组转换为字符串，元素用逗号分隔。
- `slice(startIndex, endIndex)`：从数组中提取指定范围的元素，返回一个新数组，不修改原数组。
- `flat(depth)`：将多维数组扁平化，depth 表示扁平化的层级，默认为 1。


// 数组的增删改查：

```javascript
替换数组的数据
let array = [1, 2, 3, 4, 5, 6];
array.splice(0, 2, 'a', 'b');//splice(startIndex,deleteCount,item)
console.log(array);//['a','b',2,3,4,5,6]

增加数据
let nums = [1, 2, 3, 4, 5, 6];
nums.splice(0, 0, 1);//splice(startIndex,deleteCount,item)
console.log(nums);//[1, 1, 2, 3, 4, 5, 6]

删除数据
let nums1 = [1, 2, 3, 4, 5, 6];
nums1.splice(2, 2);//splice(startIndex,deleteCount,item)=》[3,4]
console.log(nums1);//[1,2,5,6]

搜索索引
let nums2 = [1, 2, 3, 4, 5, 2, 6];
console.log(nums2.indexOf(2));
console.log(nums2.lastIndexOf(2));

删除头元素
let nums = [1,2,3,4,5]
nums.shift()

删除尾元素
let nums = [1,2,3,4,5]
nums.pop()

let array = [1, 2, 3, 4, 5, 6];

// 删除数组的最后一个元素
array.splice(-1, 1);//splice(startIndex,deleteCount,item)

新增头元素
let nums = [1,2,3,4,5]
nums.unshift()

新增尾元素
let nums = [1,2,3,4,5]
nums.push(1)



// 求和
let sum = [1, 2, 3, 4, 5, 2, 6];
let answer = sum.reduce((pre, cur) => pre + cur, 0); //0-》起始索引
console.log(answer);

// 条件过滤
let array2 = [1, 2, 3, 4, 5, 2, 6];
let condition = array2.filter((i) => i % 2 == 0);
console.log(condition);//[2,4,6]

const array = [1, 2, 3, 4, 5];

const deletedItems = array.splice(1, 3);
console.log(deletedItems); //[2, 3, 4]
console.log(array); //[1, 5]
```


注意
1.slice，包头不包尾复制新数组，不修改原来的数组
2.浅拷贝有哪些（不是在原数组上修改的）：
1. `slice(startIndex, endIndex)`：`slice` 方法用于创建一个新数组，其中包含原数组的一部分元素，但它是浅拷贝，不会影响原始数组。

   ```
   javascriptCopy code
   const originalArray = [1, 2, 3, 4, 5];
   const copiedArray = originalArray.slice();
   ```

2. `concat(array2, array3, ...)`：`concat` 方法用于将多个数组合并成一个新数组，不会修改原始数组。

   ```
   javascriptCopy code
   const array1 = [1, 2, 3];
   const array2 = [4, 5, 6];
   const combinedArray = array1.concat(array2);
   ```

3. 扩展运算符 (`...`)：使用扩展运算符可以复制数组并创建一个新数组。

   ```
   javascriptCopy code
   const originalArray = [1, 2, 3];
   const copiedArray = [...originalArray];
   ```

4. `Array.from(array)`：`Array.from` 方法可以从类似数组或可迭代对象创建一个新的数组副本。

   ```
   javascriptCopy code
   const originalArray = [1, 2, 3];
   const copiedArray = Array.from(originalArray);
   ```

这些方法都会创建原数组的浅拷贝，意味着它们复制了数组中的元素，但不会复制元素本身的引用。如果数组中包含对象或其他引用类型的元素，复制后的新数组和原数组将共享这些对象的引用。如果需要深拷贝，可以使用递归或第三方库来实现。
