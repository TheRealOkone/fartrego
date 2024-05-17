2024-05-14 01:16
Tags: #z

___
# Решение
### 1) [[Recursion]]
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
Исходя из свойств [[Binary Search Tree]], мы знаем что наименьший элемент находится слева, используя рекурсивный проход мы проходимся в порядке возрастания значения узлов, где мы уменьшаем счетчик "шагов" до нужного элемента. Если счетчик достиг нуля, то мы нашли нужный элемент (в случае если мы уменьшаем счетчик перед проверкой).
#### Код
```java
class Solution {
  int res = 0;
  int z = 0;

  public int kthSmallest(TreeNode root, int k) {
    z = k;
    rec(root);
    return res;
  }

  public void rec(TreeNode root) {
    if (root.left != null) rec(root.left);
    z--;
    if (z == 0) {
      res = root.val;
      return;
    }
    if (root.right != null) rec(root.right);
  }
}
```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/kth-smallest-element-in-a-bst/description/)
- [neetcode видео решения](https://youtu.be/5LUXSvjmGCw)