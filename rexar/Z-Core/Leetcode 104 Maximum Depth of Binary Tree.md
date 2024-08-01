2024-07-30 02:32
Tags: #z

___
# Решение
### 1) [[Recursion]]
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
Спускаемся по рекурсии вниз, когда достигаем дна возвращаем 1, дальше добавляем уровень из максимальной глубины дочерних элементов.
#### Код
```java
class Solution {

    public int maxDepth(TreeNode root) {
        if (root == null) return 0;
        int left = maxDepth(root.left);
        int right = maxDepth(root.right);
        return Math.max(left, right)+1;
    }
}
```
### 2)
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение

#### Код
```java

```
___
### Zero-Links
- 

___
### Links
- [leetcode задача]()
- [neetcode видео решения]()