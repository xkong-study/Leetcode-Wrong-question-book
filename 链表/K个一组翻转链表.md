这种题就是把第一层的逻辑写了然后往下迭代一层就好了。

```javaScript
var reverseKGroup = function(head, k) {
    let dummy = new ListNode(0, head);
    let pre = dummy;
    let cur = head;
    let count = 0;
    let temp = head;
    while (temp) {
        count++;
        temp = temp.next;
    }

    while (count >= k) {
        let start = pre;
        let end = cur;
        for (let i = 0; i < k; i++) {
            let next = cur.next;
            cur.next = pre;
            pre = cur;
            cur = next;
        }
        start.next = pre;
        end.next = cur;
        pre = end;
        count -= k;
    }
    return dummy.next;
};

```
