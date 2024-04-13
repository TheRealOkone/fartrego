2024-04-04 20:28
Tags: #z

___
# Решение
### 1) [[HashMap]] & Sorting
Сложность: `O(n log n)`
#### Объяснение
Создаем HashMap с ключем в виде отсортированного слова (гарантия анаграммности). Каждое слово сортируется, и проверяется есть ли такое же в словарике. Если есть то добавляется **не отсортированное** слово в значения.
#### Код
```java
class Solution {
  public List < List < String >> groupAnagrams(String[] strs) {
    Map < String, List < String >> map = new HashMap < > ();
    for (String str: strs) {
      char[] chars = str.toCharArray();
      Arrays.sort(chars);
      String sortedString = new String(chars);

      if (!map.containsKey(sortedString)) map.put(sortedString, new ArrayList < > ());
      map.get(sortedString).add(str);
    }
    return new ArrayList < > (map.values());
  }
}
```

___
### Zero-Links
- [[00 Sorting]]

___
### Links
- [[Arrays & Hashing]]