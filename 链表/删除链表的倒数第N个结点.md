# [19. 删除链表的倒数第 N 个结点](https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/)

```js
function removeNthFromEnd(head, n) {
  // 构造一个哑结点，防止出现 n 与链表长度相同
  let dummy = new ListNode(0, head);
  // 快慢指针指向哑结点
  let slow = dummy,
    fast = dummy;

  // 先让快指针走 n 步
  for (let i = 0; i < n; i++) {
    fast = fast.next;
  }

  // 快慢指针一起前进
  while (fast && fast.next) {
    fast = fast.next;
    slow = slow.next;
  }

  // 删除快指针
  slow.next = slow.next.next;
  // 返回链表
  return dummy.next;
}
```
