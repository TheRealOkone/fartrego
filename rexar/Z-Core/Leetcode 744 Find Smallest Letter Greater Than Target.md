2024-07-26 00:00
Tags: #z

___
# Решение
### 1) [[Binary Search]]
Сложность: `O(log n)`
Память: `O(1)`
#### Объяснение
Используем бинарный поиск, без условия на "элемент нашелся", таким образом, `l` показывает на следующий элемент так как `l=mid+1`. Выход за пределы массива контрится благодаря `l%n`.
#### Код
```java
class Solution {
    public char nextGreatestLetter(char[] letters, char target) {
        int n = letters.length;
        int l = 0, r = n-1;

        while (l<=r) {
            int mid = l+(r-l)/2;
            if (target < letters[mid]) r=mid-1;
            else l=mid+1;
        }
        return letters[l%n];
    }
}
```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/find-smallest-letter-greater-than-target/description/)
- [neetcode видео решения]()