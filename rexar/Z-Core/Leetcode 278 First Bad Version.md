2024-07-25 18:17
Tags: #z

___
# Решение
### 1) [[Binary Search]]
Сложность: `O(log n)`
Память: `O(1)`
#### Объяснение
Ищем с помощью бинарного поиска последнюю хорошую версию и возвращаем индекс после нее.
#### Код
```java
public class Solution extends VersionControl {
    public int firstBadVersion(int n) {

        if (isBadVersion(1)) {
            return 1;
        }

        int l = 1;
        int r = n;

        while (l < r) {
            int mid = l + (r - l) / 2 + 1;
            if (!isBadVersion(mid)) {
                l = mid;
            } else {
                r = mid - 1;
            }
        }

        return r + 1;

    }
}
```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/first-bad-version/description/)
- [neetcode видео решения]()