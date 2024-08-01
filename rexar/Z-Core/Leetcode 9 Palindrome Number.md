2024-07-16 22:21
Tags: #z

___
# Решение
### 1) Веселая нарезка цифр
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
Нарезаем последнюю цифру и кидаем в новое собираемое зеркальное число, перед этим двигаем разряды влево. В итоге сравниваем числа.
#### Код
```java
class Solution {
    public boolean isPalindrome(int x) {
        if (x < 0) return false;
        if (x == 0) return true;
        if (x % 10 == 0) return false;
        int tmp = x;
        int y = 0;
        while (tmp > 0) {
            y = y*10+tmp%10;
            tmp/=10;

        }
        return x == y;
    }
}
```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/palindrome-number/description/)
- [neetcode видео решения](https://www.youtube.com/watch?v=yubRKwixN-U)