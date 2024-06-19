2024-06-15 12:20
Tags: #z

___
# Решение
### 1) [[Bit Manipulation]]
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
Копируем крайний правый бит переменной `n` в правый крайний бит `res`. После этого у `res` сдвигаем биты влево на 1, а у `n` в право на 1. Повторять до победного.
#### Код
```java
public class Solution {
  // you need treat n as an unsigned value
  public int reverseBits(int n) {
    int res = 0;
    for (int i = 0; i < 32; i++) {
      res = (res << 1) | (n & 1);
      n = n >> 1;
    }
    return res;
  }
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/reverse-bits/)
- [neetcode видео решения](https://youtu.be/UcoN6UjAI64)