2024-04-01 23:13
Tags: #z

___
# Решение
### 1) [[HashMap]]
Сложность: `O(n)`
#### Объяснение
Создается HashMap где сначала проходим первую строку и увеличиваем счетчик буквы. Далее проходим вторую строку где уменьшается счетчик. После всего проходимся по HashMap и смотрим везде ли счетчик равен 0, т.е. в количестве букв нет разницы.
#### Код
```java
class Solution {
  public boolean isAnagram(String s, String t) {
    Map < Character, Integer > map = new HashMap < > ();
    for (char c: s.toCharArray()) {
      map.put(c, map.getOrDefault(c, 0) + 1);
    }
    for (char c: t.toCharArray()) {
      map.put(c, map.getOrDefault(c, 0) - 1);
    }

    for (int val: map.values()) {
      if (val != 0)
        return false;
    }
    return true;
  }
}
```
### 2) Sorting
Сложность: `O(n log n)`
#### Объяснение
Сортируется строки и затем сравниваются, если они равны значит наборы букв тоже равны.
#### Код
```java
class Solution {
    public boolean isAnagram(String s, String t) {
        char[] sChars = s.toCharArray();
        char[] tChars = t.toCharArray();
        
        Arrays.sort(sChars);
        Arrays.sort(tChars);
        
        return Arrays.equals(sChars, tChars);
    }
}
```
___
### Zero-Links
- [[00 Sorting]]

___
### Links
- [leetcode задача](https://leetcode.com/problems/valid-anagram/description/)
- [neetcode видео решения](https://www.youtube.com/watch?v=9UtInBqnCgA)
- [[Arrays & Hashing]]