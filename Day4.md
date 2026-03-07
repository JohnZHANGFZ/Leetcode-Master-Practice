# 链表 part 2
## 24.两两交换链表中的节点
### 重点
* 如何设置和移动cur指针
* 更改指针指向的顺序

### 补充
在我原来的实现中：

```{java}
class Solution {
    public ListNode swapPairs(ListNode head) {
        ListNode dummy = new ListNode();
        dummy.next = head;
        ListNode cur = dummy;

        if (head == null || head.next == null){
            return head;
        }

        while (cur.next != null && cur.next.next != null){
            ListNode first = cur.next;
            ListNode second = first.next;
            ListNode temp = second.next;
            cur.next = second;
            second.next = first;
            first.next = temp;
            cur = first;
        }
        return dummy.next;
    }
}
```

判断头结点的代码为多余，其判断条件已经包含在while条件中，可删去。

## 19.删除链表的倒数第N个结点
以下是我的实现，方法为双指针：

```
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode();
        dummy.next = head;
        ListNode front = dummy;
        ListNode cur = dummy;
        for (int i = 0; i<n + 1; i++){
            front = front.next;
        } 
        while(front != null){
            cur = cur.next;
            front = front.next;
        }
        cur.next = cur.next.next;
        return dummy.next;
    }
}
```

## 160.相交链表
实现思路较为清晰明了，主要难点在于实际代码较长容易犯下错误如null pointer error

## 142.环形链表2
整体的思考逻辑懂了，但是代码实现上还需要自己再尝试一下。













