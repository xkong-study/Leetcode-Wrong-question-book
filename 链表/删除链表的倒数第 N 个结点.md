解题思路：分为快慢指针，快指针要比慢指针多走n+1个位置，每次删除的时候都要考虑特殊情况---删除头节点的时候，一定要设置虚拟头节点为0

我的错误写法：

```javaScript
ar removeNthFromEnd = function(head, n) {
let answer = new ListNode(null,head)
let quick = answer
let slow = answer
for(let i=0;i<=n;i++){
    quick = quick.next
}
while(quick){
     slow = slow.next
     quick = quick.next
}
slow.next = slow.next.next
return answer.next
}

```

let answer = new ListNode(null,head)和let answer = new ListNode(0,head)的区别，必须要是有效节点要不是删掉头节点的时候就会有问题。
