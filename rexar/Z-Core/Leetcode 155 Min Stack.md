2024-04-11 17:42
Tags: #z

___
# Решение
### 1) [[Stack]]
Память: `O(n)`
#### Объяснение
Главная идея в том что мы храним два [[Stack]], первый сохраняет числа как обычный стек. Второй сохраняет минимальное значение на момент добавления нового элемента.
В функции `push` записываем элемент, сравниваем если текущий элемент меньше минимума и потом пихаем минимум.
В функции `pop` вызываем `pop` у обоих стеков, и если стеки пустые, то перезаписываем минимальный элемент на максимальное значение, иначе обновляем актуальный минимум.
#### Код
```java
class MinStack {

  Stack < Integer > digits = new Stack < > ();
  Stack < Integer > minSt = new Stack < > ();
  int min = Integer.MAX_VALUE;

  public MinStack() {}

  public void push(int val) {
    digits.push(val);
    if (val < min) min = val;
    minSt.push(min);
  }

  public void pop() {
    digits.pop();
    minSt.pop();
    if (digits.isEmpty()) min = Integer.MAX_VALUE;
    else min = minSt.peek();
  }
  a
  public int top() {
    return digits.peek();
  }

  public int getMin() {
    return minSt.peek();
  }
}
```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/min-stack/description/)
- [neetcode видео решения](https://youtu.be/qkLl7nAwDPo)