2024-07-25 22:23
Tags: #z

___
# Решение
### 1) 
Сложность: `O(1)`
Память: `O(1)`
#### Объяснение
Если концы четные - "сжимаем" до нечетных, таким образом приводим просчет к одному виду.
#### Код
```java
class Solution {
    public int countOdds(int low, int high) {
        if (high % 2 == 0) high--; 
        if (low % 2 == 0) low++; 
        int res = (high - low)/2+1;
        return res;
    }
}
```
### 2)
Сложность: `O(1)`
Память: `O(1)`
#### Объяснение

#### Код
```java
class Solution {
    public int countOdds(int low, int high) {
        return (high + 1) / 2 - low / 2;
    }
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/count-odd-numbers-in-an-interval-range/description/)
- [neetcode видео решения]()