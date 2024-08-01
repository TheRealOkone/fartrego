2024-04-01 23:13
Tags: #z

___
# Решение
### 1) Array
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
Считаем буквы, если после в массиве не все нули, значит отличаются слова.
#### Код
```java
class Solution {
    public boolean isAnagram(String s, String t) {
        int[] dic = new int[26];
        for (char c : s.toCharArray()) dic[c-'a']++;
        for (char c : t.toCharArray()) dic[c-'a']--;
        return Arrays.stream(dic).boxed().noneMatch(x->x!=0);
    }
}
```
### 2) [[HashMap]]
Сложность: `O(n)`
#### Объяснение
Создается HashMap где сначала проходим первую строку и увеличиваем счетчик буквы. Далее проходим вторую строку где уменьшается счетчик. После всего проходимся по HashMap и смотрим везде ли счетчик равен 0, т.е. в количестве букв нет разницы.
#### Код
```java
class Solution {
    public boolean isAnagram(String s, String t) {
        Map<Character, Integer> map = new HashMap<>();
        for (char c : s.toCharArray()) map.merge(c, 1, Integer::sum);
        for (char c : t.toCharArray()) map.merge(c, -1, Integer::sum);
        for (int v : map.values()) {
            if (v != 0) return false;
        }
        return true;
    }
}
```
### 3) Sorting
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