2024-07-30 01:43
Tags: #z

___
# Решение
### 1) StreamApi
Сложность: `O(n*j)`
Память: `O(1)`
#### Объяснение
Слова излишни
#### Код
```java
class Solution {
    public int maximumWealth(int[][] accounts) {
        return Arrays.stream(accounts)
        .mapToInt(x -> IntStream.of(x).sum())
        .max()
        .getAsInt();
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