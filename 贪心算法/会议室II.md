给定一个会议时间安排的数组，每个会议时间都会包含开始和结束的时间 [[s1,e1],[s2,e2],...]（以24小时格式），si < ei。需要编写一个函数，计算并返回安排所有会议所需的最小会议室数量。

示例：
输入: [[0, 30],[5, 10],[15, 20]]

输出: 2

解释:

第一个会议从0到30小时，需要一个会议室。
第二个会议从5到10小时，与第一个会议时间重叠，因此需要一个新的会议室。
第三个会议从15到20小时，可以在第二个会议结束后在同一个会议室进行，所以不需要新的会议室。


转换为上下车问题!!!:上车+1，下车-1

```code
var minMeetingRooms = function(intervals) {
let nums = new Array(1001).fill(0);
for(let i=0;i<nums.length;i++){
    nums[nums[i][0]]+=nums[i][0];
    nums[nums[i][1]]-=nums[i][0];
}
let max = 0;
let count = 0;
for(let value of nums){
    count+=value;
    max =Math.max(max,count);
}
return max;
};
```
