2024-07-14 18:05
Tags: #z

___
# Решение
### 1) [[Sliding window]] && [[Set]]
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
Проходимся по строке в цикле и добавляем символы, при этом считаем максимум. Если символ уже находился в строке (проверка на наличие в множестве/сете), то в цикле `while` мы удаляем символы пока не избавимся от дубликата.
#### Код
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        Set<Character> set = new HashSet<>();
        int head = 0;
        int max = 0;
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            while (set.contains(c)) {
                set.remove(s.charAt(head));
                head++;
            }
            set.add(c);
            max = Math.max(max, set.size());
        }
        return max;
    }
}
```
### 2) [[Sliding window]] && [[Set]]
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
Используется массив, где индексом является номер буквы в ASCII, а значение индекс этой буквы в строке. Если встречается буква, которая уже была "добавлена", то индекс `left` поменяет значение на позицию дубликата + 1. Таким образом избавляемся от дубликата. На каждом шагу пересчитывается максимум и обновляется индекс буквы.

Это решение быстрее, чем [[#1) Sliding window && Set|1]], т.к. процесс отбрасывания неактуальной части происходит за одну операцию, а не за каждый символ.

#### Код
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
    int n = s.length();
    int maxLength = 0;
    int[] charIndex = new int[128];
    
    for (int left = 0, right = 0; right < n; right++) {
        left = Math.max(charIndex[s.charAt(right)], left);
        maxLength = Math.max(maxLength, right - left + 1);
        charIndex[s.charAt(right)] = right + 1;
    }
    
    return maxLength;
    }
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача]()
- [neetcode видео решения]()