2024-06-01 18:09
Tags: #z

___
# Решение
### 1) [[Dynamic Programming]]
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
В начале проверяем на невалидность строки из-за нуля в начале. ~~проверку можно сделать и в цикле на 2 нуля, но пофиг~~
Для работы алгоритма, требуется запоминать предыдущее и предпредыдущее количество комбинаций.
В цикле мы добавляем пред и предпредыдущие комбинации, если они соответствуют условию. 
- Предыдущее добавляется, если текущая цифра != 0.
- Предпредыдущая добавляется, если две последние цифры создают число 10-26.
Возвращаем в итоге последнее значение (предудущее, т.к. текущее)
#### Код
```java
class Solution {

  public int numDecodings(String s) {
    if (s.charAt(0) == '0')
      return 0;
    int n = s.length();

    int prevPrev = 0;
    int prev = 1;
    for (int i = 0; i < n; i++) {
      int cur = 0;
      if (s.charAt(i) != '0')
        cur += prev;
      if (i >= 1) {
        if (s.charAt(i - 1) == '1' ||
          (s.charAt(i - 1) == '2' && s.charAt(i) < '7'))
          cur += prevPrev;
      }
      prevPrev = prev;
      prev = cur;
    }
    return prev;
  }
}
```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/decode-ways/)
- [neetcode видео решения](https://www.youtube.com/watch?v=dAeTMDCpEtE)
- [Леонид Волков сладкое решение](https://www.youtube.com/watch?v=dAeTMDCpEtE)