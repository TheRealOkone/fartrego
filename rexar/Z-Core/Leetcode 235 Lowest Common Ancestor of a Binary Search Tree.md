2024-05-12 23:10
Tags: #z

___
# Решение
### 1) [[Binary Search Tree]]
Сложность: `O(log n)` если сбалансировано, иначе `O(n)`
Память: `O(1)`
#### Объяснение
Если данные 2 значения оба меньше или оба больше текущего элемента, то мы сдвигаемся по ветви влево или вправо, повторяем пока выполняются эти условия.
Как только эти условия перестали выполняться - элемент найден.
#### Код
```java
class Solution {
  public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
    if (root == null) return null;
    if (p.val < root.val && q.val < root.val) {
      return lowestCommonAncestor(root.left, p, q);
    } else if (p.val > root.val && q.val > root.val) {
      return lowestCommonAncestor(root.right, p, q);
    } else
      return root;
  }
}
```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/description/)
- [neetcode видео решения](https://youtu.be/gs2LMfuOR9k)