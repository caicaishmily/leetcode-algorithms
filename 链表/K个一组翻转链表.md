# [25. K 个一组翻转链表](https://leetcode-cn.com/problems/reverse-nodes-in-k-group/)

```js
function reverseKGroup(head, k) {
  // 如果链表节点为空或是只有头结点本身 直接返回 head
  if (head === null || head.next === null) {
    return head;
  }

  /* 反转区间 [left, right) 的元素，注意是左闭右开 */
  const reverse = (left, right) => {
    let pre = null,
      cur = left,
      nxt = right;
    while (cur !== right) {
      nxt = cur.next;
      cur.next = pre;
      pre = cur;
      cur = nxt;
    }
    // 返回反转后的头结点
    return pre;
  };

  // 区间 [a, b) 包含 k 个待反转元素
  let a = (b = head);

  for (let i = 0; i < k; i++) {
    // base case 如果不足 k 个，则不需要反转
    if (b === null) return head;
    b = b.next;
  }

  // 反转前 k 个元素
  let newHead = reverse(a, b);
  // 递归反转后续链表并将子链表连接起来
  a.next = reverseKGroup(b, k);

  return newHead;
}
```
