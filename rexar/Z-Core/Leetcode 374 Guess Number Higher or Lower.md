2024-07-25 01:25
Tags: #z

___
# Решение
### 1) [[Binary Search]]
Сложность: `O(log n)`
Память: `O(1)`
#### Объяснение
Слова излишни
#### Код
```java
public class Solution extends GuessGame {
    public int guessNumber(int n) {
        int l=1, r = n;
        while (l <= r) {
            int mid = l+((r-l) >> 2);
            int g = guess(mid);
            if (g == 0) return mid;
            if (g == -1) r = mid-1;
            if (g == 1) l = mid+1;
        }
        return 0;
    }
}
```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/guess-number-higher-or-lower/)
- [neetcode видео решения]()