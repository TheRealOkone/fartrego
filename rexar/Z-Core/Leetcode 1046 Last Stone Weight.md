2024-06-10 11:49
Tags: #z

___
# Решение
### 1) [[Heap OR Priority Queue]]
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
Просто берется приоритетная очередь, т.к. хранит в себе объекты отсортировано, и может иметь дубликаты. Берется **ненулевая** разность двух самых больших чисел по модулю и возвращается в очередь. В конце возвращаем самое большое число, если в очереди что-то осталось.
#### Код
```java
class Solution {
  public int lastStoneWeight(int[] stones) {
    PriorityQueue < Integer > q = new PriorityQueue < > ((a, b) -> b - a);
    for (int stone: stones) q.offer(stone);
    while (q.size() > 1) {
      int x = q.poll();
      int y = q.poll();
      int res = Math.abs(x - y);
      if (res != 0) q.offer(res);
    }
    return q.peek() != null ? q.poll() : 0;
  }
}
```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/last-stone-weight/description/)
- [neetcode видео решения](https://youtu.be/B-QCq79-Vfw)