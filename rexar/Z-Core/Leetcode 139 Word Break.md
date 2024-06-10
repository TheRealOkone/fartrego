2024-06-07 20:13
Tags: #z

___
# Решение
### 1) [[Dynamic Programming]] && [[Tries (Prefix Tree)]]
Сложность: `O(n)`
Память: `O(n^2*m)`
#### Объяснение
В задаче используется метод [[Memoization]] для запоминания "можем ли мы с такой-то позиции успешно дорешать задачу". Поэтому мы проходимся по главному слову с конца в начало.
На каждой букве, мы пытаемся подобрать, есть ли такое слово в словаре, которое входит в главную строку с этой позиции.
- Если такое слово есть, то мы мемоизируем, что с этой позиции у нас успешность результата, как с позиции после этого слова. Т.е. если мы нашли слово в условной середине главного слова, то мы записываем, а можем ли мы дособирать слова после.
Также если слово уже найдено, то проверка остальных слов пропускается.
В результате мы доходим до начала слова и получаем результат.
#### Код
```java
class Solution {
    public boolean wordBreak(String s, List<String> wordDict) {
        boolean[] dp = new boolean[s.length() + 1];
        dp[s.length()] = true;

        for(int i = s.length()-1; i >= 0; i--){
            for(String w: wordDict){
                if((i + w.length()) <= s.length() && s.startsWith(w, i)){
                    dp[i] = dp[i + w.length()];
                }
                if(dp[i]){
                    break;
                }
            }
        }
        return dp[0];
    }
}

```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/word-break/description/)
- [neetcode видео решения](https://youtu.be/Sx9NNgInc3A)