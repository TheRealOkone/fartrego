2024-04-12 01:12
Tags: #z

___
# Решение
### 1) [[Stack]]
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
В задаче гарантируется, что входящее выражение верное. Значит, если встречается не число, то гарантируется, что стек хранит 2 числа. Получаем 2 числа, проводим арифметическую операцию и записываем в стек. После прохода всего цикла в стеке останется результат.
#### Код
```java
class Solution {
  public int evalRPN(String[] tokens) {
    Stack < Integer > st = new Stack < > ();
    for (String tk: tokens) {
      try {
        int number = Integer.parseInt(tk);
        st.push(number);
      } catch (Exception ignored) {
        int right = st.pop();
        int left = st.pop();
        if (tk.equals("*")) st.push(left * right);
        if (tk.equals("/")) st.push(left / right);
        if (tk.equals("+")) st.push(left + right);
        if (tk.equals("-")) st.push(left - right);
      }
    }
    return st.pop();
  }
}
```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/evaluate-reverse-polish-notation/)
- [neetcode видео решения](https://youtu.be/iu0082c4HDE)