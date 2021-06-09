# [230. 二叉搜索树中第 K 小的元素](https://leetcode-cn.com/problems/kth-smallest-element-in-a-bst/)

```js
// 利用二叉搜索树的中序遍历是一个已经排序好的结构
function kthSmallest(root, k) {
  let res = null;

  const inOrderTraverse = (node) => {
    if (node !== null && k > 0) {
      // 先遍历左子树
      inOrderTraverse(node.left);
      // 中序遍历的位置
      if (--k === 0) {
        res = node.val;
        return;
      }
      // 后遍历右子树
      inOrderTraverse(node.right);
    }
  };

  inOrderTraverse(root);

  return res;
}
```
