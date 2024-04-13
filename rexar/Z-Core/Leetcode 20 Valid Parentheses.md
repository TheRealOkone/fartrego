2024-04-11 16:25
Tags: #z

___
# Решение
### 1) [[Stack]]
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
Создаем стек. Проходимся по строке. Если символ является открывающейся скобкой, то кладем в стек, если закрывающейся то, проверяем не пустой ли стек, а также является ли скобка парной. Если да, то все ок, алгоритм работает дальше, иначе возвращаем `false`, так как не валидно.
В конце возвращаем результат пустоты стека, так как может оставаться лишняя скобка, если число было нечетным.
#### Код
```java
class Solution {
  public boolean isValid(String s) {
    Stack < Character > st = new Stack < > ();
    Map < Character, Character > openBrackets = new HashMap < > ();
    openBrackets.put(')', '(');
    openBrackets.put(']', '[');
    openBrackets.put('}', '{');

    for (char c: s.toCharArray()) {
      if (openBrackets.containsValue(c)) st.push(c);
      else if (st.isEmpty() || st.pop() != openBrackets.get(c)) return false;
    }

    return st.isEmpty();
  }
}
```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/valid-parentheses/)
- [neetcode видео решения](https://youtu.be/WTzjTskDFMg)